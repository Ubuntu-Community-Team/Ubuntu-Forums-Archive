---
title: "Cannot open terminal window as UBUNTU restarts"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by chikkubhai on 2007-07-10
Hi,

I have been using windows for the past 10 years. I am planning to learn Linux and so installed latest XUBUNTU on a old system: HP pavilion 510c, 1.3GHz celeron, 256mb ram and 40GB hard drive.  The installation was clean. 

I was learning pretty fine, and then I had to to click the terminal window option to learn the usage of BASH or whatever by going to  Applications\Accessories\Terminal
and then the whole XUBUNTU restarts itself asking me to login again and again.

The monitor is an IBM - P260.

Looks like I have to revert back to Windows again.

Any help for this newbie?

Regards
Kris

---

### Post by jordanmthomas on 2007-07-10
This certainly isn't a solution, but it may help you debug your situation:
press Alt + F2 (this does run apps in xfce, no?)
type
```
xterm
``` and hit enter.

Now you have a terminal at least.  Try running ```
xfce4-terminal >> ~/Desktop/output
``` from this and see if you can catch any errors (they'll be in a file called output on your desktop)

Note, running xfce4-terminal may crash your session even if run from the xterm, so save any work first.

---

### Post by chikkubhai on 2007-07-10
he hee :)

I just found another way to restart my system. No dude, thanks for the quick  help, but, it restarted again.

Output, a document on the desktop, shows nothing in it though!

Any other idea??

And whats xfce no??

---

### Post by jordanmthomas on 2007-07-10
It's 4:30 in the morning here, so I can't really think of anything else right now to help.  Try looking up how to read logs (they're in /var/log/Xorg.0.log and /var/log/Xorg.0.log.old).  
(hint, use a text editor and open them up)

If you find anything in them that seems like it might be an error post them here and perhaps someone can help.  As for me, it's off to bed now.

As for the xfce no question...Xubuntu uses [xfce]("http://www.xfce.org/") as its environment.  I wasn't sure if Alt + F2 would actually do anything.  I guess xfce, no? could have been written as "xfce, am I correct?"

---

### Post by chikkubhai on 2007-07-10
Good night Thomas, 

As suggested by you, I am pasting all of the two file contents to figure out why opening the terminal window restarts my XUBUNTU

Unfortunately, I can only show part of the text from the log files as the thread does not allow more than 40,000 character long messages. Instead I am attaching the two log files you requested. Ill be waiting for you to wake up.. :) Just kidding.

Aaargh.. Ubuntu file uploader cannot recongize ".log" files and just adding '.txt' and uploading doesn't work either as Ubuntu cannot upload more than 19.5 kb text files. I am uploading them as a tar file 'TerminalCrashLogFiles.tar' now.


/var/log/Xorg.0.log   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux radhakrishna-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 10 01:32:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "IBM P260"
(**) |   |-->Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
.
.
.............  not the end.. see the attached log files in the tar file for full text

---

### Post by Super TWiT on 2007-07-10
When you booted off the CD that you had, did you check the disk for errors?  There should be an option to check the disk for errors or something to the extent of that.

P.S.  Regular Ubuntu will run on those specs as I have gotten a laptop to run quite smoothly with it and its specs are as follows: Pentium III and 192 MB of RAM.  The CPU clock speed was somewhere around 500 MHz.

---

### Post by chikkubhai on 2007-07-12
no. I didnot. Now that I already installed it, what should I do?

---

### Post by jordanmthomas on 2007-07-12
It appears to be an issue with fonts or libxaa.
```


Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules//libxaa.so [0xb7b07fbd]
3: /usr/bin/X [0x8109799]
4: /usr/bin/X [0x815fea7]
5: /usr/bin/X [0x815b0f0]
6: /usr/bin/X(ValidateGC+0x25) [0x809a135]
7: /usr/bin/X [0x816067c]
8: /usr/bin/X [0x8160aaf]
9: /usr/bin/X [0x815c211]
10: /usr/bin/X(compPaintWindowBackground+0x6d) [0x80f614d]
11: /usr/bin/X(miWindowExposures+0xfa) [0x8111a1a]
12: /usr/bin/X [0x80daf7c]
13: /usr/bin/X(miHandleValidateExposures+0x78) [0x8129388]
14: /usr/bin/X(MapWindow+0x3aa) [0x8078fda]
15: /usr/bin/X(ProcMapWindow+0x59) [0x808bf69]
16: /usr/bin/X [0x8142531]
17: /usr/bin/X(Dispatch+0x19f) [0x808c61f]
18: /usr/bin/X(main+0x495) [0x8074785]
19: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d5febc]
20: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```

I'm not sure what to do here with this, but this is the backtrace of your crash.
I have only one suggestion but you will lose all your settings for xfce (panels, wallpaper, etc and you'll have to set them up again)
Use an xterm since your xfce4-terminal is borked.
```
cd
mkdir backup
mv .xf* backup

```
log out and back in and see if it may help.  If not, you can get all your settings back by copying the files in your backup folder you just made back into your home directory.

Good luck.

EDIT:  there's nothing stopping you from learning bash though.  You could use another terminal, like xterm for example until you get this issue resolved.

---

### Post by chikkubhai on 2007-07-25
Could not fix this problem. Is there any solution to this at all???

---

### Post by Super TWiT on 2007-08-03
I guess the only thing to do now is to reinstall.  You could have gotten a bad CD somehow and I would suggest to re download the image and burn another CD using the new image.

---

### Post by ugm6hr on 2007-08-03
**Don't reinstall.**

If you installed Xubuntu7.04 from the AlternateCD, then this is a known issue.  Have a search on Launchpad.

As mentioned - there should be no problem with alternative Terminals - aterm, eterm, xterm... (available from Synaptic, I think).  Then uninstall xfce4-terminal.

---

### Post by Super TWiT on 2007-08-03
Sorry, for offering bad advice.  I hope he didn't reinstall yet.:)  I forgot that you could download different terminals.

---

### Post by ugm6hr on 2007-08-03
> **Super TWiT said:**
> Sorry, for offering bad advice.  I hope he didn't reinstall yet.:)  I forgot that you could download different terminals.

Not that reinstalling was going to cause a problem (given he'd just done a fresh install) - it just wouldn't have solved the problem either!

---

### Post by GranPaSmurf on 2007-10-02
I am having the same problem. I am a total Linux/newbie. I am building a file server for my network, using Xubuntu. I am following some fine step-by-step instructions on:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
But when I got to the point of opening Terminal, I got knocked back to the start-up screen. I re-installed Xbuntu & tested Terminal before uninstalling any packages, just in case. Same problem.
If I understand previous answers, I can just use xterm instead, in fact, did I understand to uninstall Xfce? Am I losing anything usefull? Is it downloadable from site later?
dk

---

### Post by jordanmthomas on 2007-10-02
If you uninstall xfce from Xubuntu you'll be left with no graphical environment.  For me, on a server this would be no big loss since I'd just ssh into it anyway.  For you, it could be a devastating loss.

But yes, if you DO uninstall xfce it can be reinstalled later with
```
sudo aptitude install xubuntu-desktop
```

---

### Post by GranPaSmurf on 2007-10-03
[https://answers.launchpad.net/ubuntu/+source/xfce4-terminal/+question/7143](https://answers.launchpad.net/ubuntu/+source/xfce4-terminal/+question/7143)
has answer that worked for me

---

