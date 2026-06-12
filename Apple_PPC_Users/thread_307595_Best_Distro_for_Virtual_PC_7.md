---
title: "Best Distro for Virtual PC 7?"
date: 2006-11-26
forum: Apple PPC Users
---

### Post by galvatron1983 on 2006-11-26
Im having to stick with my trusty ol PowerBook G4 for a little longer then I thought so I need to make the best of what I have before making the step up to a MacBook Pro and all its Linux-running-natively-in-a-Mac-OS X-window glory. 

Im just wondering if anybody here could suggest a distro that works best with Microsoft Virtual PC 7. Ive tried Ubuntu 5.10, it installed to a virtual machine ok but it was terribly slow, much slower then my Win XP virtual machine. Im tempted to try and install mandriva under VPC 7. Any ideas?

Im running a 17" PBG4 1.5ghz, 512MB RAM

---

### Post by stmiller on 2006-11-26
I've had many problems with recent distros in VPC7. I finally gave up out of frustration. I'd suggest an xfce focused distro if I were you. Good luck.

---

### Post by EuroCity on 2006-11-27
Yes, Virtual PC and Linux has always been a little problematic - but not impossibile, if one likes to experiment...

The main problem with VPC 7 (and 2004, and previous versions also) is that its colour depth is limited to 16 bits: so, for example, live CDs which default to 24-bit colour come up with distorted graphics. 

Usually this can be corrected by switching to a console with ctrl-alt-f2 and then editing the /etc/X11/xorg.conf file (with nano/pico, vi or similar), substituting 16 to 24 in the DefaultDepth setting; then, one can return to the main screen with ctrl-alt-f7, logout and restart X (ctrl-alt-del) to get good graphics.

Sadly, in the Ubuntu 6.10 Desktop CD the f2 console outpout is strangely distorted, too (not a black screen with a command prompt, as it should be), so one must do a *sudo dpkg-reconfigure xserver-xorg* from within the Terminal in the f7 distorted 24-bit screen (which is, anyway, more readable after having returned from the f2 virtual console). The Alternate CD, sadly, is not usable with 6.10 (too big configuration windows, thus unusable).

With Fedora Core 6, one must do a text-based install and then, logging in as root, edit /etc/inittab to default to runlevel 5 instead of 3 (and create new users afterwards); the graphical installer defaults to 24 bit (thus, distorted graphics, even if one could actually use that only for the install) and there's probably no way to change this; it also crashes near the end of the install.

Mandriva 2007 only works with the One CD kernel (use the virtual console trick, but there is only vi, with its strange commands, in Mandriva, so it's more difficult for newbies).

Debian 4.0 and OpenSUSE 10.2 I've yet to try, when their final versions will come out in December.

All in all, Linux in Virtual PC 7 is slow, but certainly usable for experimenting.

See also [http://vpc.visualwin.com](http://vpc.visualwin.com) for more info (it is based on the Windows VPC 2004 version, but many things also apply to the Mac VPC 7, of course)...

---

### Post by galvatron1983 on 2006-11-27
Thanks a lot for the advice, I cant wait to get a MacBook Pro and be able to emulate Linux at full speed using parallels software, but until then I want to try and experiment with VPC7. 

Im gonna try and install Mandriva One 2007 and let you know how I get on .

---

### Post by EuroCity on 2006-11-29
Mandriva 2007, actually, is relatively fast on Virtual PC 7 (together with Fedora Core 6; Ubuntu 6.10 is a little slower, maybe).

BTW, I forgot to say that in VPC one must set the time to Local Time (not UTC); and, also, use the Virtual Switch networking mode (the Shared one usually doesn't work with Linux). The clock, anyway, tends to remain in sync with the OS X clock in recent distros, so there isn't any time sync problem anymore (except when you resume the virtual machine from a Saved State: in such a case, you must manually re-sync the Linux time with an NTP server from within the VM). It could also be a good thing to set up an user with the same UID and GID as in Mac OS X: which is usually 501 (the first user created when one installs OS X). If a resolution larger than 1024x768 is wanted, one must use the VESA driver instead of the S3 one. Personally, for simplicity, I don't usually set up a swap partition in my Linux VPC images, but format them as one root (/) partition; then, after the installation, one can always create a swapfile with the *dd* command.

The ways to set up all this may be different in the various distros, of course...

---

### Post by galvatron1983 on 2006-11-29
Ive had trouble with the graphics settings in VPC while running Mandriva 2007, all I get is a garbled mess, I know its to do with the 24bit default colour depth. How do I change the colour depth from 24 to 16 before the live cd boots into the desktop??

---

### Post by EuroCity on 2006-11-29
You must do it *after* the Live CD boots into the desktop; when it has finished booting into the garbled mess, do this:

**ctrl-alt-f2** (to switch into a virtual console)

**vi /etc/X11/xorg.conf** (at the root command prompt)

... and then scroll down to the DefaultDepth line in the Xorg configuration file, where you should insert 16 instead of 24: now, this is a little difficult in vi (sadly, there seems to be no pico/nano in Mandriva One), but essentially one switches to "insert mode" by pressing the **i** key and then one puts the cursor under the numbers to be edited; to save the changes and exit, press the **Esc** key and get into "command mode", digiting **:wq** (or **:q!** if you did some mistake and don't want to save the changes). I'm certainly no vi expert, so others might have better instructions on how to do this...

When you have edited the file, do a

**ctrl-alt-f7**

to return to the garbled screen, and then log out (if possible graphically, otherwise with ctrl-alt-del); maybe, after, you must do another ctrl-alt-del to modify the login screen resolution (I don't remember exactly); the Live CD user login name is **guest** (and no password), IIRC.

A little difficult in the beginning, but easy once done...

---

### Post by galvatron1983 on 2006-11-29
At the moment Im having trouble getting virtual pc 7 to recognise an F2 keypress. Being on a Powerbook, every time I press the f2 key even when Im clearly "inside" the mandriva virtual machine, I activate the Mac os X volume control. I think this is overriding its usage in Virtual PC. Is there a way I can work around this?

---

### Post by EuroCity on 2006-11-29
A **ctrl-alt-fn-f2** (instead of **ctrl-alt-f2**) should do it...

---

### Post by galvatron1983 on 2006-11-29
Its ok I disable the function keys volume control. But when I went into the virtual console, I logged in as guest. Then I did the vi /etc/x11/xorg.conf and pressed enter. All I got was a screen filled with blue ~ symbols down the left side of the screen with /etc/x11/xorg.conf [New Directory] at the bottom.....

---

### Post by EuroCity on 2006-11-29
You must login as root in the virtual console: IIRC, it is already a root prompt with the # sign; otherwise, if logged in as guest, type **su** and then the enter key (no password). The real login as guest is afterwards, from the main login screen, after having restarted the X server with the new 16-bit settings.

The file to edit is, of course, **/etc/X11/xorg.conf** (with an uppercase "X").

---

### Post by galvatron1983 on 2006-11-29
Ok I successfully got into the xorg.config file via vi, I edited the defaultdepth to 16, typed in :wq and i got the message "etc/X11/xorg.config 106L, 2750C written" so i assume i saved it. I then did ctrl-alt-f7, returned back to the garbled mess screen, logged out of the current session, then returned to the log in screen, which was still a garbled mess. I logged in as guest, and was presented with the same garbled mess desktop. I dont think the x11 window server was reset from the log out. Im not sure what to do....

---

### Post by EuroCity on 2006-11-29
When you get to the the garbled mess login screen, try to do *another* ctrl-alt-del, before logging in: this should solve the problem (in other words, the login screen itself must be OK before you log in). Otherwise, there must be some problem with the xorg.conf file and you should return to editing it.

I did all this more than a month ago, so I don't remember exactly how it was: anyway, sooner or later it works.

---

### Post by galvatron1983 on 2006-11-29
If I do another ctrl-alt-delete it just asks me if I want to restart the computer, wouldnt that mean the xorg.conf file would return to its original state, this being a live cd?? Perhaps if I installed the live cd permanently to the virtual machine, then restarted after editing the xorg.conf file, the change would be permanent and a restart would give me a 16bit colour depth desktop.

---

### Post by EuroCity on 2006-11-29
Yes, if you restart you will lose all changes. Maybe the xorg.conf file didn't get edited properly? You could try to open it again in vi. Otherwise, you could always try to install the system from the CD, with the distorted screen (it should be readable, at least) and then make the changes to the installed system.

Or, even better: you could open a terminal in the distorted live desktop and type su, and then gedit (or kwrite, or kate: depends on which CD you have) /etc/X11/xorg.conf - no vi needed, in this way.

Anyway, I'll have to try the Mandriva installation again myself: maybe there's something I don't remember so well. But I got it working after some experimenting.

... BTW, now I think I remember: aren't there some configuration screens before booting into the GNOME or KDE desktop? Did you pass them in distorted mode, then? Maybe you should simply restart and (re)do the /etc/X11/xorg.conf thing *before* entering anything in the first of these screens: this should be the easiest way, with 16-bit colour from the very beginning of the graphical setup.

---

### Post by galvatron1983 on 2006-11-29
this was my screen in the mandriva virtual machine after I edited the xorg.conf file. 

As you can see I tried a "start x" command that didnt work. Startx usually resets the x window server. 

[IMG]http://i17.tinypic.com/2j4tzdc.jpg[/IMG]

---

### Post by EuroCity on 2006-11-29
Aha: I think you must edit *all* the references to 24-bit colour depths into 16-bit colour depths, in that file - that should fix things!

Maybe, anyway, it would be better to reboot and start over again...

---

### Post by galvatron1983 on 2006-11-29
Success! These are the settings I used for the xorg.conf file.....

[IMG]http://i11.tinypic.com/2vsrzon.jpg[/IMG]

---

### Post by EuroCity on 2006-11-29
Ah, good! :D 

Maybe, also let us know about your install and usage experience, afterwards... :cool:

---

### Post by galvatron1983 on 2006-11-29
Ive been using Mandriva 2007 in VPC7 for a couple of hours now and Ive been quite suprised by how good the experience is. It is slow......but not too bad, Firefox takes around 40 seconds to launch, but the desktop is very responsive. Ive allocated 224MB system ram and 16mb video ram to the virtual machine, and Ive just modified the xorg.conf file again to allow a resolution of 1440x900, the native resolution of my Powerbooks screen. At the moment Im trying to get it to use my Macs internet connection, any ideas on getting that to work??

---

### Post by EuroCity on 2006-11-30
As I said before, networking must be set up in the Virtual Switch mode (Shared networking usually doesn't work with Linux in VPC); to do this, shut down the virtual machine from within Mandriva 2007, and then go to its Settings panel in VPC: set the networking to Virtual Switch, save, and then start Mandriva 2007 again.

Some time ago (Mandriva 2006), I tried it also with my iBook G4, and it worked perfectly through the wireless AirPort interface.

---

### Post by Railsbuntu on 2008-04-16
Hi guys,

I have a Mac G4, and for testing purposes I have installed Win2000 using VP7, and it works quite well.

Tomorrow I will be installing Ubuntu 7.10 in VPC, and inside that Ubuntu VM, I will install Xen that will also craete other VMs, I don't know in which mess I am gonna end up.

Anyone tried that before? :)

---

### Post by slacka-vt on 2008-04-16
If I'm not mistaken, VPC simulates an x86 environment.
So why try to run a distro that offers a version that runs natively on a PPC ?
True you will have to reboot, but compare that to the speed you run at in VPC.
Of course it's going to be slow. The PPC version of Ubuntu
will blow the doors off the same version of Ubuntu X86 running
in VPC.

Another option would be to run KDE4 your Mac OS.
They've even created install packages for all the great KDE apps:
[KDE4 on MAC OS X]("http://techbase.kde.org/index.php?title=Projects/KDE_on_Mac_OS_X") 

~s

---

### Post by Railsbuntu on 2008-04-17
Yeah I was thinking about that. Is there a virtual machine for Osx that runs PPC operating systems like ubuntu?

By the way I don't to run any GUI linux, I simply want to simulate a server environment, so I will only be using the command line.

---

### Post by Railsbuntu on 2008-04-17
I tried installing Ubuntu 7.10 x86 using a CD and Debian 4 x86 using an iso image, and both seem to hang up during installation while validating a apckage.

For Ubuntu it hang up when validating gzlib

For debian it hang up when validating vim-tiny


What could be the problem?


EDIT: wow after a very long while, it finally got through, sorry about that, everything is working fine currently.

---

### Post by Railsbuntu on 2008-04-17
Gasp, the installation failed: could not find an installable kernel in the package.

---

### Post by slacka-vt on 2008-04-17
Probably mixed up because it is a virtualized X86 environment.

~s

---

### Post by Railsbuntu on 2008-04-17
I've been investigating a lot, and it seems that VPC7 has very very bad support for Linux distros anyway. Some people have managed to install some Linux distros, but they went through a lot of trouble.

There are some tutorials on the net, most of them are written for VPC 2004 / 2007 which only run on Intel processors, so there is no cpu emulation going on.

---

### Post by slacka-vt on 2008-04-17
> There are some tutorials on the net, most of them are written for VPC 2004 / 2007 which only run on Intel processors, so there is no cpu emulation going on.


Ok . . . .I'll bite.
VPC on an Intel Mac ?!?
That's emulating X86 architecture on an X86 machine.
Windows and Ubuntu are both designed and supported for Intel processors to begin with,
why is there any need for virtualization  ?
An Intel Mac can run Windows apps with Parallels and VMWare and can be dual booted into any number of Linux distros.
Am I missing something here ?

BTW,  I've been running VPC 7 (2007 addition) on my PPC G5 Mac for 2 years now  for the sole purpose of keeping up on my DOS commands up to snuff. I run Win2K on it. :lolflag:

~s

---

### Post by Railsbuntu on 2008-04-18
I have a PowerPC Mac.

And virtualization fulfills a completely different need that dual booting. I need virtualization.

---

