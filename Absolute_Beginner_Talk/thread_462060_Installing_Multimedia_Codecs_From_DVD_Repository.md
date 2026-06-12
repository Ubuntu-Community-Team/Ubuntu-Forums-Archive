---
title: "Installing Multimedia Codecs From DVD Repository"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by oed301 on 2007-06-02
Hai ...
I'm a new user of ubuntu...(Feisty Fawn):D
and my ubuntu don't have internet connection:(
so i'm using ubuntu dvd repository:)

 [ubuntu guide ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")
when i try to install Multimedia Codecs 

i got this
:(


[B]oed@spongkeh:~$ sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
> gstreamer0.10-plugins-bad gstreamer0.10.pitfdll
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find package "gstreamer0.10.pitfdll".  However, the following
packages contain "gstreamer0.10.pitfdll" in their name:
  gstreamer0.10-pitfdll 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--16:46:09--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving optusnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Name or service not known.
--16:46:09--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Name or service not known.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--16:46:13--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving optusnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Name or service not known.
--16:46:13--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Name or service not known.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfiguredhttp://ubuntuforums.org/images/smilies/icon_sad.gif
:(
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras

[/B]




[SIZE="5"]Please...help me to solve this problem .....[/SIZE]

---

### Post by jrib on 2007-06-02
the msttcorefonts package just downloads ttf files from somewhere which fails since you don't have internet connection.  You also made a typo in your command.  It should be "gstreamer0.10-pitfdll" not "gstreamer0.10.pitfdll".  Solution: 1.  Fix your typo and 2. don't install msttcorefonts, just download the ttf's you want with another computer and drop them in ~/.fonts.

---

