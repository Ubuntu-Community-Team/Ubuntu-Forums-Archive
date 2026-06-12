---
title: "msttcorefont"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by lich 6222 on 2007-05-06
Hi !
I tried to get Msttcorefonts , but got error ay time i trying to dowloads them.
I know its in multiverse and multiverse is enabled in my system.
I am in israel .
I dont mind to use any other font , i just need the ability to use  *Hebrew fons*
any sugestion ?
 BTW using ubuntu 06.10
eli

---

### Post by taurus on 2007-05-06
Can you at least post the command that you ran and the complete error message?  Did you use this guide to install it?

[https://help.ubuntu.com/community/RestrictedFormats/Microsoft%20Fonts](https://help.ubuntu.com/community/RestrictedFormats/Microsoft%20Fonts)

---

### Post by lich 6222 on 2007-05-06
Thank you !
i will look at the link,
last try was with msttcorefonts_2.0_all.deb
got a lot of error message when try to run it.
 I dont know how to get  afile with all message error 

eli
 btw my menu is part in hebrew 
hebrew character are inside bios  but not availble in abiword or open office

---

### Post by lich 6222 on 2007-05-06
Thank you i trid the command in the terminal but got some error.
i am conecting to the net with adsl and via a proxi server
 the botom line was "

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-xfree86-nonfree (4.2.1-3) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
opendir: No such file or directory



it seem the program trued to dowload from third party 


eli@eli-desktop:~$ sudo apt-get install msttcorefonts ttf-xfree86-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
Suggested packages:
  xserver-xfree86 xfs-xtt xfs
&#1492;&#1495;&#1489;&#1497;&#1500;&#1493;&#1514; &#1492;&#1495;&#1491;&#1513;&#1493;&#1514; &#1492;&#1489;&#1488;&#1493;&#1514; &#1492;&#1493;&#1500;&#1499;&#1493;&#1514; &#1500;&#1492;&#1497;&#1493;&#1514; &#1502;&#1493;&#1514;&#1511;&#1504;&#1493;&#1514;:
  ttf-xfree86-nonfree
0 &#1502;&#1513;&#1493;&#1491;&#1512;&#1490;&#1497;&#1501;, 1 &#1502;&#1493;&#1514;&#1511;&#1504;&#1497;&#1501; &#1495;&#1491;&#1513;&#1497;&#1501;, 0 &#1497;&#1493;&#1505;&#1512;&#1493; &#1493;-0 &#1500;&#1488; &#1497;&#1513;&#1493;&#1491;&#1512;&#1490;&#1493;.
1 &#1500;&#1488; &#1502;&#1493;&#1514;&#1511;&#1504;&#1493;&#1514; &#1500;&#1495;&#1500;&#1493;&#1496;&#1497;&#1503; &#1488;&#1493; &#1492;&#1493;&#1505;&#1512;&#1493;.
&#1510;&#1512;&#1497;&#1498; &#1500;&#1511;&#1489;&#1500; 435kB &#1502;&#1514;&#1493;&#1498; &#1492;&#1488;&#1512;&#1499;&#1497;&#1493;&#1504;&#1497;&#1501;.
&#1488;&#1495;&#1512;&#1497; &#1508;&#1512;&#1497;&#1505;&#1492; 1073kB &#1504;&#1493;&#1505;&#1508;&#1497;&#1501; &#1497;&#1492;&#1497;&#1493; &#1489;&#1513;&#1497;&#1502;&#1493;&#1513;.
WARNING: The following packages cannot be authenticated!
  ttf-xfree86-nonfree
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse ttf-xfree86-nonfree 4.2.1-3 [435kB]
Fetched 435kB in 17s (24.2kB/s)             
Selecting previously deselected package ttf-xfree86-nonfree.
(Reading database ... 119096 files and directories currently installed.)
Unpacking ttf-xfree86-nonfree (from .../ttf-xfree86-nonfree_4.2.1-3_all.deb) ...
Setting up msttcorefonts (2.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--04:20:00--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--04:20:10--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--04:20:20--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--04:20:30--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--04:20:40--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--04:20:50--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--04:21:00--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--04:21:10--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--04:21:20--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--04:21:30--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--04:21:40--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--04:21:50--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--04:22:00--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory


Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)



eli

---

### Post by neodarksaver on 2007-05-06
I would suggest u to get automiatix2, just google for it.

it can install many programs for u, including the font. Michael Dell uses it, even though i hate dell computers.

---

### Post by lich 6222 on 2007-05-06
***************
I would suggest u to get automiatix2, just google for it.

it can install many programs for u, including the font. Michael Dell uses it, even though i hate dell computers.
- Show quoted text -
***************

~
thank you!
I did find the program automatix2 (yiu mispelled an extra i)
i dowloade it and install it
i tryed to install "skyep" but the instalation fail in the stage of msttcorefonts

I think thst the instable conection to internet may be the cause


eli

---

### Post by mul14 on 2007-11-14
I have same problem with you. how to uninstall msttcorefont? error message always appear when install any package..
I'm using fresh ubuntu gutsy gibbon.

---

