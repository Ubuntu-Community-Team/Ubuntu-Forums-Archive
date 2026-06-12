---
title: "Help to install on Mac PPC"
date: 2009-08-16
forum: Apple Hardware Users
---

### Post by B_Free on 2009-08-16
I have an iMac 266 w/256 ram, a Power Mac 450 G4 with 512 ram, 1.25 MMD w/ 1.5 g ram. None of which I can install (6.10, 8.04, 9.04) on. The monitors are Starlogic 19" and a 22" Acer flat screen.

I have owned Macs since 1989. I don't know much about the Terminal app. I know when you put an install disc in and restart holding down the C key, an install icon is there ready to install.

My problem is there is nothing there at the end. The iMac is the only computer that even makes an attempt. The CDs are PPC and burnt in disc utility to make a live CD.

Is there anyone out there that can help?!

---

### Post by marshag63 on 2009-08-17
Try downloading the alternate install CD for PPC.  Are you burning them as .iso, otherwise they won't run.

Have a look at this post as well:

[http://ubuntuforums.org/showthread.php?t=1215305](http://ubuntuforums.org/showthread.php?t=1215305)

MarshaG63

---

### Post by B_Free on 2009-08-18
Yes, I am burning an image of the iso file in Disc Utility. Most every variety of Ubuntu PPC. I wanted to see what the OS looked like on my machine(s). I have purchased 5 books, all seem to only speak of an Intel hardware. I installed an old version of Virtual PC 3.0 on the iMac. It was the first time (it has been months) I saw a installer window. Unfortunately, not enough space for me to install it.
I have typed "live video=ofonly" when prompted. The cd is heard working. The end result is always the same, a plain dark screen.

---

### Post by warreno on 2009-08-20
Huh. You're pretty brave, I have to say.

Does [this]("https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3") help at all?

More generally there's the overall install [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ"), which I'm sure you've seen. I'm intrigued to know of your successes or frustrations, since I have a G3 iBook I'd like to resurrect.

---

### Post by B_Free on 2009-08-20
Go to another post where I presume the problem.

[http://ubuntuforums.org/showthread.php?t=1195260](http://ubuntuforums.org/showthread.php?t=1195260)
 
The pre-made disc opened in my old Virtual PC app. Maybe the computer doesn't recognize CD-W.

---

### Post by warreno on 2009-08-20
It shouldn't open in *any* part of the MacOS, if you're trying to *boot* from it. The disc should be in the CD drive, with cmd-c pressed during bootup, in order to load the installer off the CD. You shouldn't see the Finder at all during any step of the Linux install process.

If the cmd-c trick doesn't work, try pressing and holding down cmd-shift-opt-delete during startup.

Hope this helps a little...

---

### Post by B_Free on 2009-08-20
> **warreno said:**
> It shouldn't open in *any* part of the MacOS, if you're trying to *boot* from it. The disc should be in the CD drive, with cmd-c pressed during bootup, in order to load the installer off the CD. You shouldn't see the Finder at all during any step of the Linux install process.

If the cmd-c trick doesn't work, try pressing and holding down cmd-shift-opt-delete during startup.

Hope this helps a little...

That is how I've been doing it for 20 years. If the CD is not recognized as a start up disc (in start up preferences OS X 10.5) or with OS 8.6, the control panel (Start up drive), the disc is not a bootable Start UP disc.

---

### Post by warreno on 2009-08-20
Well, I guess you don't need anyone's help here, then. Good luck with it.

---

### Post by B_Free on 2009-08-20
Thank you! I didn't want to sound ungrateful.

---

### Post by urosg3 on 2009-08-20
Give chance to Debian. I have no luck to install any Ubuntu on G3. No way. With Debian alternate net installer, works great.

---

### Post by llamabr on 2009-08-20
Yes, I just popped in here to recommend debian as well.  I run it on my ibook g3.  Ubuntu gave up on ppc not long ago, so I gave up fighting with the installer.

debian lenny went on with no problems, played sound, found my airport card, etc.

---

### Post by B_Free on 2009-08-21
Where can I get a copy? Does it install from a command line? I am not proficient with UNIX.

---

### Post by urosg3 on 2009-08-21
[http://www.debian.org/CD/netinst/]("http://www.debian.org/CD/netinst/")
Here

---

### Post by urosg3 on 2009-08-21
@B_Free
When you are ready, i can drive you through installation. Let me know when.

Cheers

---

### Post by B_Free on 2009-08-21
Thanks! I just got 3 more books on Linux. Just need to read the install versions. Ubuntu is a new language for me. I was never good in French class.

---

### Post by warreno on 2009-08-24
> **B_Free said:**
> Thank you! I didn't want to sound ungrateful.

I should apologize for my tone; it was uncalled-for. Having had more than a few head-desk episodes over the years with difficult OS installs, I can understand just how frustrating it is to want to get something done and not have it happening.

I'm still intrigued by your experiments; if I'm reading correctly, Debian is working for you on your older PPC Macs. I've got an iBook G3/600 with 640 MB RAM that might be a candidate for Debian -- do you have an analogous system, and is Debian working on it?

Again, sorry for being snotty before.

---

### Post by urosg3 on 2009-08-25
> **warreno said:**
> 

I'm still intrigued by your experiments; if I'm reading correctly, Debian is working for you on your older PPC Macs. I've got an iBook G3/600 with 640 MB RAM that might be a candidate for Debian -- do you have an analogous system, and is Debian working on it?


This is my Powerbook working great with Debian

G3 on 400 Mhz Lombard
256 RAM
8 MB video RAM
DVD bay

---

### Post by warreno on 2009-08-25
Huh. Well that's nothing but encouraging, as I see it. Groovy. Thanks.

---

### Post by B_Free on 2009-08-25
No. I haven't been able to install anything other than Mac OS X on my Macs. But stay tuned because I am getting some interesting and somewhat conflicting info from the books I purchased. The most interesting one is written by Bill Ball "Linux for your Mac" published by Prima Tech, 2001. The manner in which it is written is simplistic. I can even understand it. 
I have a few projects I am working on this week, so Ubuntu will have to wait.

---

### Post by urosg3 on 2009-08-25
@B_Free take your time, no rush.

---

### Post by urosg3 on 2009-08-25
> **warreno said:**
> Huh. Well that's nothing but encouraging, as I see it. Groovy. Thanks.

Yours Mac have plenty RAM.You can even try some easy DE like openbox and result will be impressive.

---

### Post by B_Free on 2009-08-27
What is DE?

---

### Post by urosg3 on 2009-08-28
DE = Desktop environment, like GNOME or KDE. Openbox is lite and ultra speed.

[https://help.ubuntu.com/community/Openbox]("https://help.ubuntu.com/community/Openbox")

---

### Post by B_Free on 2009-09-09
Finally! I installed Xubuntu 9.04 on my Blue and White, 300, 384 RAM, 30g HD. I read my books, and even though they varied, they had certain things in common. This was the LIVE CD.
Insert the CD, at the prompt type **help**. The screen adds a couple of paragraphs, use the **tab** key. You are given a couple dozen ideas as what to type. Type **live-nosplash-powerpc**. My screen kept scrolling with "No CD ". In order for me to stop this, I held down the **Command key (apple key) and F4 key** briefly. The live CD became live, finally! I installed the software from the desktop. I used all the defaults. I have Ubuntu. It even restarted the next day. 
Now to reconfigure the monitor and install other packages.

---

### Post by natgab on 2009-09-12
> **llamabr said:**
> Yes, I just popped in here to recommend debian as well.  I run it on my ibook g3.  Ubuntu gave up on ppc not long ago, so I gave up fighting with the installer.

debian lenny went on with no problems, played sound, found my airport card, etc.


---I have been reading this thread and wanted to load Ubuntu 9.04 on my iMac 400, 512MB RAM, 40 GB HD , 8MB video. But built in CD-ROM is a little flaky. I like how the Debian has the net install CD. I tried Live & alt install and could not get them to work, should I go and get the Debian disc instead?

I also have an ext. Firewire CD burner for it, but I guess that will only work after Ubuntu/Debian is loaded right? Unless it will work, the ext. burner is very reliable.

I previously played around with Ubuntu 7.04 on an old PC but the hardware gave out. And my widescreen monitor always needed constant adjustments :-( I like that my little iMac has std 1024x768 screen.

thanks

---

### Post by B_Free on 2009-09-13
I had trouble with the iMac also. I do have the tray loading, not the slot loading like your machine. Hold down the **c key** when starting up, just as if you are installing a Mac OS. At the first chance to type something, type **help**. Next time you can type just use** tab**. You get about a dozen or so ideas as what to type next. Type **live-nosplash-powerpc**, **return** key. It will do its thing. Go to a white screen then back to black with a flashing curser in the top left corner. If it doesn't respond with more info in about 10 seconds, use your **command (Apple key) +F4 key**. Not sure why this works, but it does. It should start doing its thing. About 10-30 seconds later you should have a pointer in the middle of your screen. Just let it go. It will be there, in time. I then install it from the desktop. I let it use all the defaults. I don't change anything.

If you like your 1024x768 resolution, you will be disappointed. There are inherent problems with the way screen resolutions are written. Goes back to all distributions. And I have them all. You can get 800x600 and that is it. The forums and my books all have solutions to the problem but each one is different, Maybe just commas, or different depths or ............ There are other problems with memory management, codecs, and more. These things I am presently trying to fix.

Do you have a high speed internet connection? If so, connect it to the machine before you install the OS. There is about 112 MB of updates to the OS. It replaces some things and updates others. It takes about as long to do the updates as it does to install. Also if you want other software, like OpenOffice that may not have been installed with the OS, this would be the time. It also updates and replaces.

---

### Post by urosg3 on 2009-09-13
B_Free, way to go! Great news.

Cheers...

p.s. on Debian i have 1024:768 resolution out of box...

---

### Post by sweetleaf on 2009-09-13
> **B_Free said:**
> If you like your 1024x768 resolution, you will be disappointed. There are inherent problems with the way screen resolutions are written. Goes back to all distributions. And I have them all. You can get 800x600 and that is it.

I have 1024x768 on my slot-loading iMac. IIRC, that's the resolution it's been using by default since the fresh Jaunty install.

(I don't mean to suggest that video "works out of the box," though. I had to play with xorg.conf to get better than 8-bit color, and to center the display properly, and . . . )

---

### Post by natgab on 2009-09-13
> **B_Free said:**
> I had trouble with the iMac also. I do have the tray loading, not the slot loading like your machine. Hold down the **c key** when starting up, just as if you are installing a Mac OS. At the first chance to type something, type **help**. Next time you can type just use** tab**. You get about a dozen or so ideas as what to type next. Type **live-nosplash-powerpc**, **return** key. It will do its thing. Go to a white screen then back to black with a flashing curser in the top left corner. If it doesn't respond with more info in about 10 seconds, use your **command (Apple key) +F4 key**. Not sure why this works, but it does. It should start doing its thing. About 10-30 seconds later you should have a pointer in the middle of your screen. Just let it go. It will be there, in time. I then install it from the desktop. I let it use all the defaults. I don't change anything.

If you like your 1024x768 resolution, you will be disappointed. There are inherent problems with the way screen resolutions are written. Goes back to all distributions. And I have them all. You can get 800x600 and that is it. The forums and my books all have solutions to the problem but each one is different, Maybe just commas, or different depths or ............ There are other problems with memory management, codecs, and more. These things I am presently trying to fix.

Do you have a high speed internet connection? If so, connect it to the machine before you install the OS. There is about 112 MB of updates to the OS. It replaces some things and updates others. It takes about as long to do the updates as it does to install. Also if you want other software, like OpenOffice that may not have been installed with the OS, this would be the time. It also updates and replaces.


---I do have fast connection for the updates. One of the notes in this thread said they used cmd-c to boot off the disc. I usually just use c to load my Mac OS on the iMac. I will be trying the Debian disc to see if its easier than the ubuntu. I will report back how I do.

thanks

---

### Post by B_Free on 2009-09-13
Just do it the way you would install a Mac OS. The only difference is the terminal prompts.

---

### Post by natgab on 2009-09-13
OK, here are my initial results with Debian CD:

1) CD-ROM reads CD data, but does not seem to work well for CD boot.

2) I used this page to try booting, but I had trouble.

[https://help.ubuntu.com/9.04/installation-guide/powerpc/boot-drive-files.html#files-newworld](https://help.ubuntu.com/9.04/installation-guide/powerpc/boot-drive-files.html#files-newworld)

3) I was able to get the open firmware screen, so then I tried OF CD boot but got an "yaboot load -sleep=0 adler32=1" error.

4) Loaded 4 files listed in above page, in my HD at root (same area as OS, not home folder) and then tried the HD boot. This gave me an "Load size is to small" error.

5)Which is the partition to list in the HD OF boot? /dev/rdisk0 or  /dev/rdisk0s10

Hope I provided enough info guys.  thanks

---

### Post by urosg3 on 2009-09-14
> 1) CD-ROM reads CD data, but does not seem to work well for CD boot.

Try this one [http://www.debian.org/CD/netinst/]("http://www.debian.org/CD/netinst/")

---

### Post by natgab on 2009-09-16
I will try again to burn a new copy of the net install CD for Debian. 

I could not get it to load. I got the error listed in my post above.  I use Mac Toast Titanium 10, as an ISO disc.  I will try this time with Disk Utility.

I hope I can boot to Debian, then I will be able to use Linux again !

---

### Post by natgab on 2009-09-20
OK,

Debian full CD loaded ok, but only get text.  I read this from Oswaldkelso to get the CD to install:

[http://forums.debian.net/viewtopic.php?t=20481](http://forums.debian.net/viewtopic.php?t=20481)

But now I have to reread it carefully to fix the xorg.conf for my iMac. In ubuntu it gives you the blue screen with white text and some presets like install to fix it. I used this when I had my Linux PC to make my widescreen monitor work.

But in Debian, I got just the " raw text " like in this (except it has my iMac info):

#tested on eMac, ATI 1.25 GHz
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
Option "XkbOptions" "lv3:lwin_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
Option "ConnectorTable" "100,1,0,1,108,2,0,1"
Option "ReverseDDC" "true"
Option "AGPMode" "4"
EndSection

And it has some text on the bottom with ^n, ^b and I don't know how to use those commands. I will read up on my books and report my progress. :P

---

### Post by B_Free on 2009-09-22
The symbol next to the n and the b is the symbol for the control key. To learn more about Unix commands this is a good (but confusing) site.
[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)
When you are there, hit the anchor to the right that says "Useful Commands". That will take you to a definition of what n and b mean in the Unix world. Vi is an editor.

---

### Post by natgab on 2009-09-23
thanks B_free,

I will have to bookmark that to learn some of the new terms.  I got info at Debian forums on what to edit in my xorg.conf file.  I have a nice Debian log-in screen. (but thats it)

I just posted this, on my newest problem:

[http://ubuntuforums.org/showthread.php?t=1273159](http://ubuntuforums.org/showthread.php?t=1273159)

thanks again

---

### Post by B_Free on 2009-09-27
This Live Cd works. It gives you the ability to choose your screen size, etc. Everything everyone has been complaining about looks to be solved. It was similar to installing Mac OS 7. It showed progress GUIs, and everything worked. At the prompt type live-powerpc and then the return key. It is the live cd version

[http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/)

[http://old-releases.ubuntu.com/releases/kubuntu/5.10/](http://old-releases.ubuntu.com/releases/kubuntu/5.10/)

I'm excited!

---

### Post by natgab on 2009-09-28
> **B_Free said:**
> This Live Cd works. It gives you the ability to choose your screen size, etc. Everything everyone has been complaining about looks to be solved. It was similar to installing Mac OS 7. It showed progress GUIs, and everything worked. At the prompt type live-powerpc and then the return key. It is the live cd version

[http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/)

[http://old-releases.ubuntu.com/releases/kubuntu/5.10/](http://old-releases.ubuntu.com/releases/kubuntu/5.10/)

I'm excited!


---You mean this old 5.10 version of (K)Ubuntu works better than the new version?  I am still stuck at the log-in screen. I added more info to my xorg.conf file (screen size, depth) and still stuck nothing.  Just a frozen log-in screen.

This is the thread, with what I have done so far:

[http://forums.debian.net/viewtopic.php?f=7&t=45343](http://forums.debian.net/viewtopic.php?f=7&t=45343)

I will download the old version, and see how it behaves. Nothing to lose, I think I'm still reinstalling about once a week. :)

---

### Post by B_Free on 2009-09-28
Do you mean you downloaded it and tried it or you are going to the old site? The maximum screen size is 1024x768. But if you look in the xorg.conf file in the 5.10, it has much more info. Info about your keyboard, mouse, etc. Why they changed, I don't know.

Just tried a few Ubuntu versions on a Windows machine given me. They (Windows) enjoy a GUI to install. No problem with resolutions. You can even install next to the Windows operating system. 
Recently, Ubuntu higher ups decided to discontinue support for PPC owners. They said there wasn't much interest in installing in a PPC machine. I now see why. If we were privy to what Windows owners enjoy, there would be a huge support for Linux. Billions and billions of dollars spent on this equipment, and no one will support us any more. So much for recycling.

---

### Post by natgab on 2009-09-29
> **B_Free said:**
> Do you mean you downloaded it and tried it or you are going to the old site? The maximum screen size is 1024x768. But if you look in the xorg.conf file in the 5.10, it has much more info. Info about your keyboard, mouse, etc. Why they changed, I don't know.

Just tried a few Ubuntu versions on a Windows machine given me. They (Windows) enjoy a GUI to install. No problem with resolutions. You can even install next to the Windows operating system. 
Recently, Ubuntu higher ups decided to discontinue support for PPC owners. They said there wasn't much interest in installing in a PPC machine. I now see why. If we were privy to what Windows owners enjoy, there would be a huge support for Linux. Billions and billions of dollars spent on this equipment, and no one will support us any more. So much for recycling.

---I will download from the link you posted. I have not yet.  I have still been tweaking the current Debian 5 verion I have on it.

Yeah, the only time I saw a nice PPC GUI install was on an old version of Yellow Dog Linux.  But it was too odd and the YDL forum seemed to only have several months old post. Not like here and the Debian forum that have new stuff on a daily basis.

And I always wondered why Linux would not embrace PPC/Apple computers more. They are a smaller set of hardware to deal with and have a Unix background.  A/UX for old stuff and OSX for the new.  

And now with eBay, old Macs are more affordable for people. I am using my iMac for Linux, precisely because I probably would not get more than $25.00 USD for it. So I decided to use it as a website tester & Linux learning computer.

---

### Post by natgab on 2009-10-01
OK,

Good and bad news. I used the Kubuntu 5.10 Breezy Badger Install CD and used plain old " install " and got a Desktop!

Perfect 1024x768 screen & sound. Applications worked, rebooted fine. This is the xorg.conf that it has, in case it helps someone:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#* *sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	   FontPath	"/usr/share/X11/fonts/misc"
	   FontPath	"/usr/share/X11/cyrillic"
	   FontPath	"/usr/share/X11/100dpi/:unscaled"
	   FontPath	"/usr/share/X11/75dpi/:unscaled"
	   FontPath	"/usr/share/X11/fonts/Type1"
	   FontPath	"/usr/share/X11/fonts/CID"
	   FontPath	"/usr/share/X11/fonts/100dpi"
	   FontPath	"/usr/share/X11/fonts/75dpi"
	   # paths to defoma fonts
	   FontPath	"/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType"
	   FontPath	"/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"


Section "Module"
   Load   "GLcore"
* *Load* *"i2c"
* *Load* *"bitmap"
* *Load* *"ddc"
* *Load* *"dri"
* *Load* *"extmod"
* *Load* *"freetype"
* *Load* *"glx"
* *Load* *"int10"
   Load   "type1"
* *Load* *"vbe"
EndSection

Section "InputDevice"
* *Identifier* *"Generic Keyboard"
* *Driver* ** *"kbd"
* *Option* ** *"XkbRules"* *"xorg"
* *Option* ** *"XkbModel"* *"pc104"
* *Option* ** *"XkbLayout"* "us"
EndSection

Section "InputDevice"
* *Identifier* *"Configured Mouse"
* *Driver* ** *"mouse"
   Option		"CorePointer"
   Option		"Device"			"/dev/input/mice"
   Option		"Protocol"			"ImPS/2"
   Option		"Emulate3Buttons"	"true"
   Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
* *Identifier* *"ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
* *Driver* ** *"ati"
   Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
* *Identifier* *"iMac"
* *Option* ** *"DPMS"
* *HorizSync	  60-60
* *VertRefresh* *75-117
EndSection

Section "Screen"
* *Identifier* *"Default Screen"
* *Device* ** *"ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
* *Monitor* ** *"iMac"
* *DefaultDepth* *24
* *SubSection "Display"
* ** *Depth* ** *1
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
* *SubSection "Display"
* ** *Depth* ** *4
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
* *SubSection "Display"
* ** *Depth* ** *8
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
* *SubSection "Display"
* ** *Depth* ** *15
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
* *SubSection "Display"
* ** *Depth* ** *16
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
* *SubSection "Display"
* ** *Depth* ** *24
* ** *Modes* ** *"800x600" "640x480"
* *EndSubSection
EndSection

Section "ServerLayout"
* *Identifier* *"Default Layout"
* *Screen* ** *"Default Screen"
* *InputDevice* *"Generic Keyboard"
* *InputDevice* *"Configured Mouse"
EndSection

Section "DRI"
* *Mode* *0666
EndSection


```

Now the bad news,

As I entered everything, I noticed that I was prompted for a user name and password, but did not get prompted for a root password?

So the thing is, when I tried to set my ethernet to my home network, I could not because I was not root. I am familiar with the KDE panels, as I used Kubuntu on a PC box for a while untill the MB died.

Is there a quick fix? I get the same thing in Command Line.

---Why did cut & paste not work right this time? I pasted the code without all those asterisks last time and now I get them?

---

### Post by natgab on 2009-10-01
Hey B_Free,

I am still working on the iMac to get it to behave.  But guess what? 

I took the 5.10 Breezy Badger Live disc to work and popped it into my Power Mac G4 533DA and of course it work perfectly. Everything works like a charm and great speed. Pretty fast for running off a CD. 

EDIT: I got it working ! 

I am running Debian Lenny 5.03. I used some of the info from the Breezy xorg.conf to get it to work. The old OS versions still have some usefull information!

Posted from my iMac on Lenny :KS

---

### Post by B_Free on 2009-10-02
If you have everything working, maybe you should share your success with everyone in a new post. Tell how you made it work. It could save many people from the frustration starting out.

---

### Post by DarianMac on 2009-11-03
Hello. I'm new the forum and do not speak good English so using Google Translate. I hope you are able to express myself as coherent. I have a PowerMac Dual G4, which I installed Ubuntu 9.04. My problem is that I do not know how to use Ubuntu and the second processor in the system, I use only one of the two. How to enable support for SMP? I understand that it takes this for Ubuntu to use more than one processor.

---

### Post by gifford on 2009-11-05
For the dual cpu G4 to work with both processors you need to use the ppc smp kernel in synaptic package manager. Just install and reboot.

---

