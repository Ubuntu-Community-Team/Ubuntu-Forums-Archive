---
title: "Help! Something Is Worong With Synaptic Package"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-27
Hello ... I was trying to install *msttcorefonts* using terminal and it outputted some errors like connection failed. I thought thier server is down ... so after that I was trying to install *firestarter,* *wine* and some other programs and they gave me the same connection failure as *msttcorefonts* output gave me ... but the thing that is driving me crazy is that they all have the SAME ERROR and the include *msttcorefonts*!!! ](*,) 
This is when I was trying to install *wine*
```
isos@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  winesetuptk
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/14.5MB of archives.
After unpacking 52.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 71030 files and directories currently installed.)
Removing winesetuptk ...
Selecting previously deselected package wine.
(Reading database ... 71027 files and directories currently installed.)
Unpacking wine (from .../wine_0.0.20050725-0ubuntu1.1_i386.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--21:21:12--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection refused.
--21:21:12--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... failed: Connection refused.
--21:21:13--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... failed: Connection refused.
--21:21:13--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... failed: Connection refused.
--21:21:13--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... 195.113.161.88
Connecting to cesnet.dl.sourceforge.net|195.113.161.88|:80... failed: Connection refused.
--21:21:14--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... failed: Connection refused.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::20|:80... failed: Network is unreachable.
andale32.exe: No such file or directory

[B]All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up wine (0.0.20050725-0ubuntu1.1) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
isos@ubuntu:~$

```
Please notice the error in bold ... 
[B]All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up wine (0.0.20050725-0ubuntu1.1) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

WHAT IS GOING ON?!!!??!! :( 

PLEASE SOMEBODY HELP!!!!

---

### Post by mjm115 on 2006-04-27
If we look a little closer at the error message, we can discover what the problem is:

> 
Resolving belnet.dl.sourceforge.net... 193.190.198.97
**Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection refused.**
--21:21:12--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'


So its not something that you're doing wrong.  Connection to where the fonts can be downloaded fail.  The fonts are not actually stored in the repository, but on third-party servers.  It may be that the server was taken down or they are doing something with it.  I have seen this happen before.  I just tried to ping the server and it times out.  It is something on the other end.  Give it a try in a few hours.

---

### Post by Isoss on 2006-04-27
OK ... What then? it's still not working ... it has been like this for hours! and what do hours have to do with solving this problem? what if it didn't work? I don't wanna reinstall ubuntu for this! 8|

---

### Post by Sef on 2006-04-27
> OK ... What then? it's still not working ... it has been like this for hours! and what do hours have to do with solving this problem? what if it didn't work? I don't wanna reinstall ubuntu for this! 8|

Sometimes you have to give it a day or so.  Best thing to do is relax and try it later.

---

### Post by manicka on 2006-04-27
Try going into Synaptic and a broken package error shoud pop up. Find the broken package (wine) and then remove it with Synaptic.

You should then be able to install wine with apt-get.

Try the msttcorefonts again at a later date, when the mirror is back up and running.

---

### Post by flyingsolo on 2006-04-27
I ran into the same problem with msttfonts and the same errors b/c of no response at sourceforge.  It isn't a matter of waiting b/c I've tried repeatedly over at least two weeks!  Maybe if they are having very big problems with their server, this might make sense.  Anyway, you can download the individual font files from sourceforge and then install them as per in earlier thread:

[http://www.ubuntuforums.org/showthread.php?t=166869](http://www.ubuntuforums.org/showthread.php?t=166869)

See the response of jagot to install the fonts.

---

### Post by Isoss on 2006-04-28
Ok guys .. this is gonna be bad if I'd just relax and wait cuz I got work to do .. I reinstalled ubuntu ... at least it was good for me to go through the installation process and the mounting and repository set up again ... anyway ... I don't think I'd dare to install msttfonts again so I'd just get them from windows or install them in some other way ...

---

