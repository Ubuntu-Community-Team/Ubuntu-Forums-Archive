---
title: "Reopenining Msttcorefonts"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by lich 6222 on 2007-05-07
hi !
I  need a solution for  " Msttcorefonts "
:popcorn: 

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=435205&goto=newpost](http://ubuntuforums.org/showthread.php?t=435205&goto=newpost)

I would suggest u to get automiatix2, just google for it.

it can install many programs for u, including the font. Michael Dell uses it, even though i hate dell computers.

:( 
eli

---

### Post by Bachstelze on 2007-05-07
Whats the question here ? I personnally suggest you to **not** use Automatix...

---

### Post by Nythain on 2007-05-07
wise advice :)

---

### Post by lich 6222 on 2007-05-07
the question is:
 how **to  download** the*" msttcorefonts*" to my computer .

:confused: 
I have several program that need this fonts and have produce error when trying to get the "msttcorfonts " from many internet adress .

---

### Post by Bachstelze on 2007-05-07
The msttcoefots package does not install the fonts. Instead, it launches a scrip that downloads them from sourceforge. If you have no net connection the msttcorefonts package is useless, just grab the files (they're in EXE format, you'll need to extract the fonts with cabextract).

---

### Post by Nythain on 2007-05-07
so what is the output if you type
sudo aptitude install msttcorefonts
in the terminal???

---

### Post by lich 6222 on 2007-05-07
> **Nythain said:**
> so what is the output if you type
sudo aptitude install msttcorefonts
in the terminal???

this what i get after many minute
:) 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libcurl3-gnutls 
The following packages have been kept back:
  cdparanoia cli-common desktop-file-utils libcdparanoia0 libcurl3 
  libgphoto2-2 libgphoto2-port0 liblircclient0 pmount rdesktop synaptic 
  vim-common vim-tiny 
0 packages upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up msttcorefonts (2.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--02:52:28--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--02:52:38--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--02:52:48--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--02:52:58--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--02:53:08--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--02:53:18--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--02:53:28--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--02:53:38--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--02:53:48--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--02:53:58--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--02:54:08--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--02:54:18--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--02:54:28--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up msttcorefonts (2.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--02:54:41--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--02:54:51--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--02:55:01--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--02:55:11--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--02:55:21--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--02:55:31--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--02:55:41--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--02:55:51--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--02:56:01--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--02:56:11--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--02:56:21--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--02:56:31--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--02:56:41--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
eli@eli-desktop:~$ 
:confused: 
botom line nothing geting inside my computer
:mad: 
Eli

---

### Post by lich 6222 on 2007-05-07
> **HymnToLife said:**
> The msttcoefots package does not install the fonts. Instead, it launches a scrip that downloads them from sourceforge. If you have no net connection the msttcorefonts package is useless, just grab the files (they're in EXE format, you'll need to extract the fonts with cabextract).
thank you !
i got 

andale32.exe  on my desktop ,
how do i  extract fonts with cabextract?

---

### Post by Bachstelze on 2007-05-07
Since it will create a bunch of other files, it's better not to put it on the desktop :

```
cd
mkdir fonts
mv Desktop/andale32.exe fonts
cd fonts
cabextract andale32.exe
```

For the other ms fonts (comic, times, arial, etc.), go to [http://corefonts.sf.net](http://corefonts.sf.net)

---

### Post by lich 6222 on 2007-05-07
thank  You!
:guitar:

---

