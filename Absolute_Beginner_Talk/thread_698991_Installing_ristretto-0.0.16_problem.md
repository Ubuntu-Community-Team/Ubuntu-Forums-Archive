---
title: "Installing ristretto-0.0.16 problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-16
Finally I got to see that I have to search for the 'keyword' shown in the ./configure step for the missing packages. I've done so to go through several steps. However, now I got 

```
checking for gtk+-2.0 >= 2.10.0... not found
*** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.10.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
```

When I searched for gtk+-2.0, it gave me nothing. So i did gtk+-, then this is what I have:
```
p   evince-gtk-dbg                     - Document (postscript, pdf) viewer (gtk versio
p   gtk-doc-tools                      - the GTK+ documentation tools                 
p   gtk-im-libthai                     - GTK+ Input Method Module using LibThai       
p   gtk-qt-engine                      - theme engine using Qt for GTK+ 2.x           
p   gtk-sharp2-gapi                    - C source parser and C# code generator for GOb
p   gtk2-engines-gtk-qt                - transitional dummy package                   
v   human-gtk-theme                    -                                              
i   libaiksaurusgtk-1.2-0c2a           - graphical interface to the Aiksaurus toolkit 
p   libaiksaurusgtk-1.2-dev            - graphical interface to the Aiksaurus toolkit 
v   libaiksaurusgtk-dev                -                                              
i   libgoffice-gtk-0-4                 - Document centric objects library - runtime fi
p   libgtk-directfb-2.0-0              - The GTK+ graphical user interface library - D
p   libgtk-directfb-2.0-dev            - Development files for the GTK+ library - Dire
p   libtracker-gtk-dev                 - GTK+ widgets for apps that use tracker - deve
v   openoffice.org-gtk-gnome           -
```

Which one is the one that I need? Thanks!

---

### Post by kaiju on 2008-02-17
hi, i'm feeling a bit guilty here, since it was me that pointed you to ristretto in the first place, and now i see that you are going through a lot of trouble trying to install it...

it seems that ristretto will indeed be included in xubuntu hardy ([http://packages.ubuntu.com/hardy/graphics/ristretto](http://packages.ubuntu.com/hardy/graphics/ristretto)), i couldn't however find any signs of it being used in gutsy.

a little bit of google gave me this page: [http://ppa.launchpad.net/xubuntu-team/ubuntu/pool/main/r/ristretto/](http://ppa.launchpad.net/xubuntu-team/ubuntu/pool/main/r/ristretto/), and i think it's safe if you just get the appropriate package for your system from there.
or, since xubuntu already comes with gnome apps anyway (just do an 'apt-cache show xubuntu-desktop' and look under "dependends" to see what gets installed by default), you could try using eog or gqview instead (both are gnome apps and both are found in the repositories).

---

