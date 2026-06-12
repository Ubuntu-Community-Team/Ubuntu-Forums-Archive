---
title: "installation error  using apt"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-27
i tried to install wordnet and follwing error encountered

ejaz@ejaz:~$ sudo apt-get install wordnet
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  wordnet-base
The following NEW packages will be installed:
  wordnet wordnet-base
0 upgraded, 2 newly installed, 0 to remove and 159 not upgraded.
1 not fully installed or removed.
Need to get 8443kB of archives.
After unpacking 28.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe wordnet-base 2.0g-12build1 [8336kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe wordnet 2.0g-12build1 [107kB]
Fetched 8443kB in 48m26s (2905B/s)

Preconfiguring packages ...
Selecting previously deselected package wordnet-base.
(Reading database ... 69338 files and directories currently installed.)
Unpacking wordnet-base (from .../wordnet-base_2.0g-12build1_all.deb) ...
Selecting previously deselected package wordnet.
Unpacking wordnet (from .../wordnet_2.0g-12build1_i386.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--19:26:41--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--19:26:47--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--19:26:52--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--19:26:57--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--19:27:07--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--19:27:12--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up wordnet-base (2.0g-12build1) ...
Setting up wordnet (2.0g-12build1) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

although i tested by command
ejaz@ejaz:~$ wnb
it opened wordnet

this error i am getting with everything which i don't install manually.
this error only encounters bu apt.how ever the program runs well

also when i boot ubuntu ,it loads modules then it says
temorary error in name resolution                                           failed

---

### Post by u04f061 on 2006-05-27
recently i installed java .same error encountered but javac command was not known.
i mean java is not installed

---

### Post by u04f061 on 2006-05-27
please answer above question plz plz.........................................................
..........................................................................................plz................................
.............................................................................................plz

---

### Post by ifokkema on 2006-05-27
[QUOTE=u04f061]Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

although i tested by command
ejaz@ejaz:~$ wnb
it opened wordnet

this error i am getting with everything which i don't install manually.
this error only encounters bu apt.how ever the program runs well

also when i boot ubuntu ,it loads modules then it says
temorary error in name resolution                                           failed[/QUOTE]

Hi,

Seems like just the download of the msttcorefonts got an error. This seems temporarely, and the wordnet packages wass installed fine.

Currently, I can't ping cesnet.dl.sourceforge.net either, but belnet.dl.sourceforge.net did fine.

You could try to run:
```
sudo dpkg --configure -a
```

To try and finish the install of msttcorefonts again.

Ivo

---

### Post by ifokkema on 2006-05-27
[QUOTE=u04f061]recently i installed java .same error encountered but javac command was not known.
i mean java is not installed[/QUOTE]

Maybe you have the wrong package. Java virtual machine is in one package, the java compiler in another. You need j2re1.4 to run Java, and j2sdk1.4 to compile java (javac).

Ivo

---

### Post by u04f061 on 2006-05-27
yes i agree u.i was confuse when some one told me to install java  compiler using
command given by someone in this forum that it was unpacking a package which is in kb's while jdk takes mbs.

also u'r commands result is below
ejaz@ejaz:~$ sudo dpkg --configure -a
ejaz@ejaz:~$
ejaz@ejaz:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  msttcorefonts
0 upgraded, 1 newly installed, 0 to remove and 158 not upgraded.
Need to get 22.1kB of archives.
After unpacking 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse msttcorefonts 1.2ubuntu2 [22.1kB]
Fetched 22.1kB in 0s (904kB/s)

Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 69828 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu2_all.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--00:38:47--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--00:38:52--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--00:38:57--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--00:39:02--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--00:39:12--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--00:39:17--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
ejaz@ejaz:~$

---

### Post by Koech on 2006-05-27
I beleive the problem is in the url [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) Either it's down or no longer exists. Try using another if you can. Seems like it's in your sources.list.

---

### Post by u04f061 on 2006-05-27
plz clarify it
Try using another if you can. Seems like it's in your sources.list.?????????????????????????????????????????

---

### Post by ifokkema on 2006-05-28
[QUOTE=Koech]I beleive the problem is in the url [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) Either it's down or no longer exists. Try using another if you can. Seems like it's in your sources.list.[/QUOTE]

It's not in the sources list. Msttcorefonts is a package that will download the fonts for you. They aren't included in the .deb package itself. The package is configured to download the fonts this way. If those upstream servers fail... the package fails to install properly.

My guess it that it's a matter of time for at least one of those servers to come back online...

Edit: I've tested all of these servers... it appears the file is screwed up somehow an many (all?) mirrors. The servers are reachable, but sourceforge is complaining: There was a problem downloading the file from ovh.dl.sourceforge.net. Please try a different mirror.

This is a problem with sourceforge / a bug in msttcorefonts.

---

### Post by u04f061 on 2006-05-28
hoe can i find the address to different server.can u give me?

---

### Post by ifokkema on 2006-05-28
[QUOTE=u04f061]hoe can i find the address to different server.can u give me?[/QUOTE]

Well, the problem is that these settings reside somewhere in the post-install script of msttcorefonts. I've just tried some different servers and these work:
[http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)

I'm really not sure about this, but you can maybe fool the script by downloading these files to /tmp and re-rerun installation. I'm not sure if it's using /tmp at all, it's just a very wild guess...

---

