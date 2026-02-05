SHELL := /bin/zsh

.PHONY: all clean kill list

LATEXMK_MATCH := latexmk[[:space:]].*-pvc

all:
	@source ~/.zshrc && lt &

list: 
	@setopt NULL_GLOB; \
	if pgrep -f "$(LATEXMK_MATCH)" > /dev/null; then \
		print "Running processes:"; \
		pgrep -af "$(LATEXMK_MATCH)"; \
	else \
		print "No running processes."; \
	fi

kill:
	@setopt NULL_GLOB; \
	processes=$$(pgrep -f "$(LATEXMK_MATCH)"); \
	if (( $${#processes} == 0 )); then \
		print "Nothing to kill."; \
	else \
		print "Removing $${#processes} processes..."; \
		pkill -f "$(LATEXMK_MATCH)"; \
	fi

clean:
	@setopt NULL_GLOB; \
	files=( \
		*.aux *.log *.out *.toc *.bbl *.blg *.dvi *.nav \
		*.snm *.vrb *.lof *.lot *.idx *.ilg *.ind *.fls *.fdb_latexmk \
		*.synctex.gz text.bcf-SAVE-ERROR text.bcf text.run.xml *.pdf \
		*.bbl-SAVE-ERROR \
	); \
	if (( $${#files[@]} == 0 )); then \
		print "Nothing to clean."; \
	else \
		print "Removing $${#files[@]} file(s)..."; \
		rm -f -- $${files[@]}; \
	fi

