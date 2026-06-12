---
title: "Uninstall of LiveTex gone wrong!!"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Eberhard on 2008-02-04
Hi guys,

I've had LiveTex installed on my system but it didnt really work so i decided to remove it when i found out that it was also available amongst the package list in "Synaptic package Manager". I simply removed the following directories:

/usr/share/tex... (5 directories that started with tex and were LateX related)
/usr/texmf/ (The install direcetory choosen when LiveTex was installed)

After this I then went to synaptic package manager and choose the LiveTex-full. However the install went wrong and know i cant start the package manager. It says:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried running it from terminal but i get:

> Setting up texlive-lang-mongolian (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-mongolian (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-finnish (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-finnish (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-uk (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-uk (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-tibetan (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-tibetan (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-generic-recommended (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-generic-recommended (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-armenian (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-armenian (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-fonts-recommended (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-fonts-recommended (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-pictures (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-pictures (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-fi (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-fi (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-fr (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-fr (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-zh (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-zh (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-fonts-extra (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-fonts-extra (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-croatian (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-croatian (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on texlive-lang-mongolian (>= 2007); however:
  Package texlive-lang-mongolian is not configured yet.
 tetex-extra depends on texlive-pictures (>= 2007-7); however:
  Package texlive-pictures is not configured yet.
 tetex-extra depends on texlive-lang-croatian (>= 2007); however:
  Package texlive-lang-croatian is not configured yet.
 tetex-extra depends on texlive-fonts-extra (>= 2007); however:
  Package texlive-fonts-extra is not configured yet.
 tetex-extra depends on texlive-lang-finnish (>= 2007); however:
  Package texlive-lang-finnish is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-lang-dutch (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-dutch (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-ko (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-ko (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-danish (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-danish (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tex4ht-common (20070717-2) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
texhash: Done.
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex4ht-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-bg (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-bg (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-vi (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-vi (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-latin (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-latin (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-mn (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-mn (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-spanish (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-spanish (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-hungarian (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-hungarian (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended; however:
  Package texlive-generic-recommended is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-lang-african (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-african (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-manju (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-manju (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-lang-arab (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-arab (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-de (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-de (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-full:
 texlive-full depends on texlive-lang-mongolian (>= 2007); however:
  Package texlive-lang-mongolian is not configured yet.
 texlive-full depends on texlive-doc-vi (>= 2007); however:
  Package texlive-doc-vi is not configured yet.
 texlive-full depends on texlive-doc-zh (>= 2007); however:
  Package texlive-doc-zh is not configured yet.
 texlive-full depends on texlive-lang-dutch (>= 2007); however:
  Package texlive-lang-dutch is not configured yet.
 texlive-full depends on texlive-pictures (>= 2007-7); however:
  Package texlive-pictures is not configured yet.
 texlive-full depends on texlive-doc-fi (>= 2007); however:
  Package texlive-doc-fi is not configured yet.
 texlive-full depends on texlive-pstricks (>= 2007); however:
  Package texlive-pstricks is not configured yet.
 texlive-full depends on texlive-lang-arab (>= 2007); however:
  Package texlive-lang-arab is not configured yet.
 texlive-full depends on texlive-lang-manju (>= 2007); however:
  Package texlive-lang-manju is not configured yet.
 texlive-full depends on texlive-lang-spanish (>= 2007); however:
  Package texlive-lang-spanish is not configured yet.
 texlive-full depends on texlive-fonts-extra (>= 2007); however:
  Package texlive-fonts-extra is not configured yet.
 texlive-full depends on texlive-lang-latin (>= 2007); however:
  Package texlive-lang-latin is not configured yet.
 texlive-full depends on texlive-doc-ko (>= 2007); however:
  Package texlive-doc-ko is not configured yet.
 texlive-full depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-full depends on texlive-lang-croatian (>= 2007); however:
  Package texlive-lang-croatian is not configured yet.
 texlive-full depends on texlive-generic-recommended (>= 2007-7); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-full depends on texlive-doc-uk (>= 2007); however:
  Package texlive-doc-uk is not configured yet.
 texlive-full depends on texlive-lang-hungarian (>= 2007); however:
  Package texlive-lang-hungarian is not configured yet.
 texlive-full depends on texlive-doc-mn (>= 2007); however:
  Package texlive-doc-mn is not configured yet.
 texlive-full depends on texlive-lang-finnish (>= 2007); however:
  Package texlive-lang-finnish is not configured yet.
 texlive-full depends on texlive-lang-tibetan (>= 2007); however:
  Package texlive-lang-tibetan is not configured yet.
 texlive-full depends on texlive-lang-armenian (>= 2007); however:
  Package texlive-lang-armenian is not configured yet.
 texlive-full depends on texlive-math-extra (>= 2007); however:
  Package texlive-math-extra is not configured yet.
 texlive-full depends on texlive-lang-african (>= 2007); however:
  Package texlive-lang-african is not configured yet.
 texlive-full depends on texlive-doc-fr (>= 2007); however:
  Package texlive-doc-fr is not configured yet.
 texlive-full depends on texlive-doc-de (>= 2007); however:
  Package texlive-doc-de is not configured yet.
 texlive-full depends on texlive-doc-bg (>= 2007); however:
  Package texlive-doc-bg is not configured yet.
 texlive-full depends on texlive-lang-danish (>= 2007); however:
  Package texlive-lang-danish is not configured yet.
dpkg: error processing texlive-full (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-latex-base (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-ru (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-ru (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
 texlive-lang-czechslovak depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-czechslovak (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-lang-italian (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-italian (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tex4ht:
 tex4ht depends on tex4ht-common (= 20070717-2); however:
  Package tex4ht-common is not configured yet.
dpkg: error processing tex4ht (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-lang-hebrew (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-hebrew (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-portuguese (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-portuguese (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-generic-extra (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-generic-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on tetex-extra | texlive-latex-base; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-font-utils (2007-12ubuntu3.1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-font-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of feynmf:
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
dpkg: error processing feynmf (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-xetex (2007-12ubuntu3.1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-xetex (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-doc-it (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-it (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-pictures; however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-extra-utils (2007-12ubuntu3.1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-extra-utils (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-lang-vietnamese (2007.dfsg.1-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-lang-vietnamese (--configure):
 subprocess post-installation script returned error exit status 1
Setting up musixlyr (2.1c-3) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
/var/lib/dpkg/info/musixlyr.postinst: 16: /usr/share/texmf/web2c/mktexupd: not found
dpkg: error processing musixlyr (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-doc-nl (2007-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-nl (--configure):
 subprocess post-installation script returned error exit status 1
Setting up musixtex (1:0.112.2-3) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing musixtex (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)


I've tried: sudo apt-get update and sudo apt-get upgrade but it does not work.

Hope you can help me

---

### Post by Anicka on 2008-02-04
Uninstalling by deleting directories is dangerous business, as you just discovered. Enough said about that, now we will have to try to fix it...

Try```
sudo apt-get -f install texlive-full
```it might help. If not, I usually find it good to start at the top and go down, so ```
sudo apt-get -f install texlive-lang-mongolian
```since that is the first package to complain. You can also try```
sudo dpkg --configure texlive-lang-mongolian
```and see if it lets you to run ```
sudo apt-get install texlive-full
```afterwards.

---

### Post by Eberhard on 2008-02-04
Ok, I've tried the what you have suggested but every time i get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

... think you are right about not deleting directories (at least for a beginner like me). It seems that the dpkg is corrupted some how and that apt-get uses dpkg. An evil circle...! Since i have not installed to much on my system yet, it would be an easy solution to just reinstall but i hope it is posible to fix without.

---

### Post by Anicka on 2008-02-04
What do you get from the command ```
dpkg -C
```?

---

### Post by Eberhard on 2008-02-04
I get:

> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 latex-xcolor         Easy driver-independent TeX class for color
 context              powerful TeX format
 tetex-extra          TeX Live: teTeX transitional package
 pgf                  TeX Portable Graphic Format
 texlive-formats-extra TeX Live: Extra formats
 texlive-bibtex-extra TeX Live: Extra BibTeX styles
 texlive-music        TeX Live: Music typesetting
 texlive-latex-recommended TeX Live: LaTeX recommended packages
 texlive-pstricks     TeX Live: PSTricks packages
 texlive-humanities   TeX Live: LaTeX support for the humanities
 texlive-math-extra   TeX Live: Advanced math typesetting
 texlive-latex3       TeX Live: LaTeX3 packages
 texlive-full         TeX Live: meta package pulling in all components of TeX L
 texlive-lang-czechslovak TeX Live: Czech/Slovak
 tex4ht               LaTeX and TeX for Hypertext (HTML) - executables
 latex-beamer         LaTeX class to produce presentations
 cm-super             TeX font package with CM (EC) in Type1 in T1, T2*, TS1, X
 feynmf               set of LaTeX macros for creating Feynman diagrams
 texlive-latex-extra  TeX Live: LaTeX supplementary packages
 tetex-bin            TeX Live: teTeX transitional package
 texlive-lang-polish  TeX Live: Polish
 texlive-doc-tr       TeX Live: Turkish documentation
 texlive-doc-th       TeX Live: Thai documentation
 texlive-games        TeX Live: Games typesetting (chess, etc)
 texlive              TeX Live: A decent selection of the TeX Live packages
 texlive-lang-indic   TeX Live: Indic
 texlive-plain-extra  TeX Live: Plain TeX supplementary packages
 texlive-doc-es       TeX Live: Spanish documentation
 texlive-doc-en       TeX Live: English documentation
 texlive-doc-el       TeX Live: Greek documentation
 texlive-omega        TeX Live: Omega
 texlive-lang-ukenglish TeX Live: UK English
 texlive-publishers   TeX Live: Support for publishers
 texlive-science      TeX Live: Typesetting for natural and computer sciences
 texlive-doc-ja       TeX Live: Japanese documentation
 texlive-doc-pl       TeX Live: Polish documentation
 texlive-doc-pt       TeX Live: Portuguese documentation

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 texlive-lang-mongolian TeX Live: Mongolian
 texlive-lang-finnish TeX Live: Finnish
 texlive-doc-uk       TeX Live: Ukrainian documentation
 texlive-lang-tibetan TeX Live: Tibetan
 texlive-generic-recommended TeX Live: Miscellaneous generic macros
 texlive-lang-armenian TeX Live: Armenian
 texlive-fonts-recommended TeX Live: Recommended fonts
 texlive-pictures     TeX Live: Packages for drawings graphics
 texlive-doc-fi       TeX Live: Finnish documentation
 texlive-doc-fr       TeX Live: French documentation
 texlive-doc-zh       TeX Live: Chinese documentation
 texlive-fonts-extra  TeX Live: Extra fonts
 texlive-lang-croatian TeX Live: Croatian
 texlive-lang-dutch   TeX Live: Dutch
 texlive-doc-ko       TeX Live: Korean documentation
 texlive-lang-danish  TeX Live: Danish
 tex4ht-common        LaTeX and TeX for Hypertext (HTML) - support files
 texlive-doc-bg       TeX Live: Bulgarian documentation
 texlive-doc-vi       TeX Live: Vietnamese documentation
 texlive-lang-latin   TeX Live: Latin
 texlive-doc-mn       TeX Live: Mongolian documentation
 texlive-lang-spanish TeX Live: Spanish
 texlive-lang-hungarian TeX Live: Hungarian
 texlive-lang-african TeX Live: African scripts
 texlive-lang-manju   TeX Live: Manju
 texlive-lang-arab    TeX Live: Arabic
 texlive-doc-de       TeX Live: German documentation
 texlive-latex-base   TeX Live: Basic LaTeX packages
 texlive-doc-ru       TeX Live: Russian documentation
 texlive-lang-italian TeX Live: Italian
 texlive-lang-hebrew  TeX Live: Hebrew
 texlive-lang-portuguese TeX Live: Portuguese
 texlive-generic-extra TeX Live: Miscellaneous extra generic macros
 texlive-font-utils   TeX Live: TeX font-related programs
 texlive-xetex        TeX Live: XeTeX macros
 texlive-doc-it       TeX Live: Italian documentation
 texlive-extra-utils  TeX Live: TeX auxiliary programs
 texlive-lang-vietnamese TeX Live: Vietnamese
 musixlyr             a MusiXTeX extension for handling lyrics
 texlive-doc-nl       TeX Live: Dutch documentation
 musixtex             Typeset music scores with TeX
 texlive-lang-greek   TeX Live: Greek typesetting
 texlive-lang-norwegian TeX Live: Norwegian
 texlive-lang-swedish TeX Live: Swedish
 lmodern              scalable PostScript and OpenType fonts based on Computer 
 texlive-lang-french  TeX Live: French
 texlive-lang-other   TeX Live: Other hyphenation files
 texlive-lang-cyrillic TeX Live: Cyrillic
 texlive-metapost     TeX Live: MetaPost (and Metafont) drawing packages
 texlive-lang-german  TeX Live: German
 texlive-doc-cs+sk    TeX Live: Czechslovak documentation


---

### Post by jan quark on 2008-02-04
what happens if you run
```

sudo dpkg --configure -a
```

---

### Post by Anicka on 2008-02-04
What would happen if you try to run this ```
sudo dpkg --configure --force-configure-any texlive texlive-latex-base
```?

---

### Post by Eberhard on 2008-02-04
To Jan Quark:
sudo dpkg -configure -a gives the LOOOONG error code in my first post. Amongst others this gives:

update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg (Second line)

... This file does not exist and i think that i might have deleted all of /etc/texmf when i was "uninstalling" the first LiveTex.

---

### Post by Eberhard on 2008-02-04
TO Anicka:
sudo dpkg --configure --force-configure-any texlive texlive-latex-base gives:
> 
dpkg: also configuring `texlive-latex-recommended' (required by `texlive')
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-latex-base (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 texlive
 texlive-latex-base
 texlive-latex-recommended

...again related to the /etc/texmf/updmap.d/00updmap.cfg, which is missing

---

### Post by Anicka on 2008-02-04
Now it's time for hard ball!!! ```
sudo dpkg --configure --force-all texlive
```If it runs well, you can exchange texlive with any package you want to force-configure (maybe not start with texlive-full as it has too many dependencies)

---

### Post by Eberhard on 2008-02-04
It worked - well sort of. I can acces the synaptic package manager again which is really great. However i'm still having problems. I ran sudo dpkg --configure --force-all texlive-full it gave me the following in the ending:

> 
Errors were encountered while processing:
 texlive-lang-indic
 texlive-plain-extra
 texlive-doc-th
 texlive-lang-ukenglish
 texlive-doc-el
 texlive-doc-en
 texlive-doc-es
 texlive-doc-pt
 texlive-doc-ja
 texlive-doc-pl
 texlive-doc-tr
 cm-super
 texlive-publishers
 texlive-latex-extra
 texlive-math-extra
 texlive-lang-polish
 texlive-latex3
 context
 texlive-lang-czechslovak
 texlive-humanities
 texlive-science
 texlive-omega
 texlive-formats-extra
 texlive-pstricks
 texlive-music
 texlive-bibtex-extra
 feynmf
 texlive-games
 tetex-extra
 tetex-extra


I then tried to force the configuration of texlive-omega. "sudo dpkg --configure --force-all texlive-omega" gives
> dpkg: texlive-omega: dependency problems, but configuring anyway as you request:
 texlive-omega depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
Setting up texlive-omega (2007-12ubuntu3.1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-omega (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 texlive-omega


Then i tried configurin livetex-latex-base since it seems that livetex omega depends on it. "sudo dpkg --configure --force-all texlive-latex-base" gives:
> Setting up texlive-latex-base (2007-10) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 texlive-latex-base


---

### Post by Anicka on 2008-02-04
Try to uninstall the texlive-latex-base, if it doesn't work to do it with apt-get try```
sudo dpkg --purge --force-all texlive-latex-base
```Then try to install it again```
sudo apt-get update && sudo apt-get install texlive-latex-base
```

---

### Post by Anicka on 2008-02-04
Also you should try to install a package called tex-common```
sudo apt-get install tex-common
```it might be the answer to the 00updmap.cfg problem

---

### Post by harak on 2008-03-10
i got the same errors after I had removed my /etc/texmf folder-- in an attempt to completely remove texlive.
After some trying several posted solutions in vain. I opened synaptic manager... marked every thing  that's related to tex including Texmaker for complete removal. then reinstalled tetex. uninstalled tetex and installed texlive...voila! no more errors!:guitar:

---

### Post by hugmenot on 2008-06-28
My advice? Go to [this page]("http://packages.ubuntu.com/search?mode=filename&suite=gutsy&section=all&arch=i386&searchon=contents&keywords=00updmap.cfg") and search for the missing files it&#8217;s complaining about. 
Download these packages, force install these packages with dpkg. If it won't because these files are missing, extract these files with archiver and  place them at the path where they are expected.
Too much work? re-install Ubuntu.
Installing any tex package usually leads to a cascade of processing steps, indexing filers, generating format files, etc. You deleted the instructions for that and now you have a bad race condition.

---

