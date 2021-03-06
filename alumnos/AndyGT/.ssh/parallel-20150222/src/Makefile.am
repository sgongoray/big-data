bin_SCRIPTS = parallel sql niceload

install-exec-hook:
	rm $(DESTDIR)$(bindir)/sem || true
	$(LN_S) parallel $(DESTDIR)$(bindir)/sem

if DOCUMENTATION
man_MANS = parallel.1 sem.1 sql.1 niceload.1 parallel_tutorial.7 parallel_design.7
doc_DATA = parallel.html sem.html sql.html niceload.html parallel_tutorial.html parallel_design.html \
	parallel.texi sem.texi sql.texi niceload.texi parallel_tutorial.texi parallel_design.texi \
	parallel.pdf sem.pdf sql.pdf niceload.pdf parallel_tutorial.pdf parallel_design.pdf
endif

# Build documentation file if the tool to build exists.
# Otherwise: Use the distributed version
parallel.1: parallel.pod
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=1 $(srcdir)/parallel.pod > $(srcdir)/parallel.1n \
	&& mv $(srcdir)/parallel.1n $(srcdir)/parallel.1 \
	|| echo "Warning: pod2man not found. Using old parallel.1"

parallel_tutorial.7: parallel_tutorial.pod
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=7 $(srcdir)/parallel_tutorial.pod > $(srcdir)/parallel_tutorial.7n \
	&& mv $(srcdir)/parallel_tutorial.7n $(srcdir)/parallel_tutorial.7 \
	|| echo "Warning: pod2man not found. Using old parallel_tutorial.7"

parallel_design.7: parallel_design.pod
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=7 $(srcdir)/parallel_design.pod > $(srcdir)/parallel_design.7n \
	&& mv $(srcdir)/parallel_design.7n $(srcdir)/parallel_design.7 \
	|| echo "Warning: pod2man not found. Using old parallel_design.7"

sem.1: sem.pod
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=1 $(srcdir)/sem.pod > $(srcdir)/sem.1n \
	&& mv $(srcdir)/sem.1n $(srcdir)/sem.1 \
	|| echo "Warning: pod2man not found. Using old sem.1"

sql.1: sql
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=1 $(srcdir)/sql > $(srcdir)/sql.1n \
	&& mv $(srcdir)/sql.1n $(srcdir)/sql.1 \
	|| echo "Warning: pod2man not found. Using old sql.1"

niceload.1: niceload.pod
	pod2man --release='$(PACKAGE_VERSION)' --center='$(PACKAGE_NAME)' \
		--section=1 $(srcdir)/niceload.pod > $(srcdir)/niceload.1n \
	&& mv $(srcdir)/niceload.1n $(srcdir)/niceload.1 \
	|| echo "Warning: pod2man not found. Using old niceload.1"

parallel.html: parallel.pod
	pod2html --title "GNU Parallel" $(srcdir)/parallel.pod > $(srcdir)/parallel.htmln \
	&& mv $(srcdir)/parallel.htmln $(srcdir)/parallel.html \
	|| echo "Warning: pod2html not found. Using old parallel.html"
	rm -f $(srcdir)/pod2htm*

# Depending on parallel.html to avoid stupid pod2html race condition
parallel_tutorial.html: parallel_tutorial.pod parallel.html
	pod2html --title "GNU Parallel tutorial" $(srcdir)/parallel_tutorial.pod > $(srcdir)/parallel_tutorial.htmln \
	&& mv $(srcdir)/parallel_tutorial.htmln $(srcdir)/parallel_tutorial.html \
	|| echo "Warning: pod2html not found. Using old parallel_tutorial.html"
	rm -f $(srcdir)/pod2htm*

# Depending on parallel_tutorial.html to avoid stupid pod2html race condition
parallel_design.html: parallel_design.pod parallel.html
	pod2html --title "GNU Parallel design" $(srcdir)/parallel_design.pod > $(srcdir)/parallel_design.htmln \
	&& mv $(srcdir)/parallel_design.htmln $(srcdir)/parallel_design.html \
	|| echo "Warning: pod2html not found. Using old parallel_design.html"
	rm -f $(srcdir)/pod2htm*

# Depending on parallel_design.html to avoid stupid pod2html race condition
sem.html: sem.pod parallel_design.html
	pod2html --title "sem (GNU Parallel)" $(srcdir)/sem.pod > $(srcdir)/sem.htmln \
	&& mv $(srcdir)/sem.htmln $(srcdir)/sem.html \
	|| echo "Warning: pod2html not found. Using old sem.html"
	rm -f $(srcdir)/pod2htm*

# Depending on sem.html to avoid stupid pod2html race condition
sql.html: sql sem.html
	pod2html --title "GNU SQL" $(srcdir)/sql > $(srcdir)/sql.htmln \
	&& mv $(srcdir)/sql.htmln $(srcdir)/sql.html \
	|| echo "Warning: pod2html not found. Using old sql.html"
	rm -f $(srcdir)/pod2htm*

# Depending on sql.html to avoid stupid pod2html race condition
niceload.html: niceload.pod sql.html
	pod2html --title "GNU niceload" $(srcdir)/niceload.pod > $(srcdir)/niceload.htmln \
	&& mv $(srcdir)/niceload.htmln $(srcdir)/niceload.html \
	|| echo "Warning: pod2html not found. Using old niceload.html"
	rm -f $(srcdir)/pod2htm*

parallel.texi: parallel.pod
	pod2texi --output=$(srcdir)/parallel.texi $(srcdir)/parallel.pod \
	|| echo "Warning: pod2texi not found. Using old parallel.texi"

parallel_tutorial.texi: parallel_tutorial.pod
	pod2texi --output=$(srcdir)/parallel_tutorial.texi $(srcdir)/parallel_tutorial.pod \
	|| echo "Warning: pod2texi not found. Using old parallel_tutorial.texi"

parallel_design.texi: parallel_design.pod
	pod2texi --output=$(srcdir)/parallel_design.texi $(srcdir)/parallel_design.pod \
	|| echo "Warning: pod2texi not found. Using old parallel_design.texi"

sem.texi: sem.pod
	pod2texi --output=$(srcdir)/sem.texi $(srcdir)/sem.pod \
	|| echo "Warning: pod2texi not found. Using old sem.texi"

sql.texi: sql
	pod2texi --output=$(srcdir)/sql.texi $(srcdir)/sql \
	|| echo "Warning: pod2texi not found. Using old sql.texi"

niceload.texi: niceload.pod
	pod2texi --output=$(srcdir)/niceload.texi $(srcdir)/niceload.pod \
	|| echo "Warning: pod2texi not found. Using old niceload.texi"

parallel.pdf: parallel.pod
	pod2pdf --output-file $(srcdir)/parallel.pdf $(srcdir)/parallel.pod --title "GNU Parallel" \
	|| echo "Warning: pod2pdf not found. Using old parallel.pdf"

parallel_tutorial.pdf: parallel_tutorial.pod
	pod2pdf --output-file $(srcdir)/parallel_tutorial.pdf $(srcdir)/parallel_tutorial.pod --title "GNU Parallel Tutorial" \
	|| echo "Warning: pod2pdf not found. Using old parallel_tutorial.pdf"

parallel_design.pdf: parallel_design.pod
	pod2pdf --output-file $(srcdir)/parallel_design.pdf $(srcdir)/parallel_design.pod --title "GNU Parallel Design" \
	|| echo "Warning: pod2pdf not found. Using old parallel_design.pdf"

sem.pdf: sem.pod
	pod2pdf --output-file $(srcdir)/sem.pdf $(srcdir)/sem.pod --title "GNU sem" \
	|| echo "Warning: pod2pdf not found. Using old sem.pdf"

sql.pdf: sql
	pod2pdf --output-file $(srcdir)/sql.pdf $(srcdir)/sql --title "GNU SQL" \
	|| echo "Warning: pod2pdf not found. Using old sql.pdf"

niceload.pdf: niceload.pod
	pod2pdf --output-file $(srcdir)/niceload.pdf $(srcdir)/niceload.pod --title "GNU niceload" \
	|| echo "Warning: pod2pdf not found. Using old niceload.pdf"

sem: parallel
	ln -fs parallel sem

DISTCLEANFILES = parallel.1 sem.1 sql.1 niceload.1 parallel_tutorial.7 parallel_design.7 \
	parallel.html sem.html sql.html niceload.html parallel_tutorial.html parallel_design.html \
	parallel.texi sem.texi sql.texi niceload.texi parallel_tutorial.texi parallel_design.texi \
	parallel.pdf sem.pdf sql.pdf niceload.pdf parallel_tutorial.pdf parallel_design.pdf

EXTRA_DIST = parallel sem sql niceload \
	sem.pod parallel.pod niceload.pod parallel_tutorial.pod parallel_design.pod \
	$(DISTCLEANFILES)
