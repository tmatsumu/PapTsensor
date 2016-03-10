###############################################################################
#                                                        Mar. 10, 2016
# Makefile for PapTsensor
# - Tomotake Matsumura  <tmatsumu@astro.isas.jaxa.jp>
# - Yuki Sakurai  <yuki.sakurai@ipmu.jp>
#
###############################################################################

FILE=draft_v000
TEX=latex
REFGREP=grep "^LaTeX Warning: Label(s) may have changed."
DVIPS=dvips -Ppdf
DVIPDF=dvipdfmx -p a4 $(FILE).dvi

UNAME := $(shell uname -s)

pdf: $(FILE).pdf
ifeq (${UNAME},Darwin)
	@open $<
else
	@acroread $<
endif

$(FILE).pdf: $(FILE).dvi
	$(DVIPDF)

$(FILE).dvi: $(FILE).aux
	(while $(REFGREP) $(FILE).log; do $(TEX) $(FILE); done)

$(FILE).aux: $(FILE).tex
	$(TEX) $(FILE)

.PHONY: clean
clean:
	rm -r -f *.aux *.dvi *.log *.out *.pdf *.tpt *.ps *.toc *.tof *.lot *.lof *.bbl *.blg thumb*.* *~ *.tex-e \#*
