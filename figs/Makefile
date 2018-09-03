.PHONY : figs linked_selection_figs local_pca_figs

figs : linked_selection_figs local_pca_figs
	
linked_selection_figs : linked-selection-guide/linked-selection-site-neutral.png linked-selection-guide/linked-selection-site-hard.png linked-selection-guide/linked-selection-site-soft.png linked-selection-guide/linked-selection-site-recent_balancing.png linked-selection-guide/linked-selection-site-old_balancing.png linked-selection-guide/linked-selection-site-introgression.png linked-selection-guide/linked-selection-site-local_adaptation.png linked-selection-guide/linked-selection-region-background.png linked-selection-guide/linked-selection-region-recurrent_sweeps.png linked-selection-guide/linked-selection-region-recurrent_introgression.png

local_pca_figs : what_is_covariance.png drosophila_2R_inversion_pcs_0.png drosophila_2R_inversion_pcs_1.png drosophila_recomb_mds_for_talk.png medicago_for_talk.png the-method-diagram-modified.png


linked-selection-guide/linked-selection-site-%.pdf : linked-selection-guide.ink.svg
	./export-layers-svg.sh $< axes site $* >$@

linked-selection-guide/linked-selection-region-%.pdf : linked-selection-guide.ink.svg
	./export-layers-svg.sh $< axes region $* >$@


## image conversion

%.pdf : %.svg
	inkscape $< --export-pdf=$@

# %.svg : %.pdf
# 	inkscape $< --export-plain-svg=$@

%.png : %.pdf
	convert -density 300 $< -flatten $@

%.gif : %.pdf
	convert -density 300 $< -flatten $@

%.png : %.svg
	convert -density 300 $< -flatten $@

%.gif : %.svg
	convert -density 300 $< -flatten $@

%.pdf : %.ink.svg
	inkscape $< --export-pdf=$@

# animated gif
%.anim.gif : $(wildcard %/*.gif)
	convert -loop 0 -delay 10 -coalesce -fuzz 2% -layers optimize $$(ls $*/*.gif) $@