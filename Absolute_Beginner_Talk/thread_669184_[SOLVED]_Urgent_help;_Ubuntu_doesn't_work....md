---
title: "[SOLVED] Urgent help; Ubuntu doesn't work..."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-16
Hi, I'm trying to dual-boot my Fujitsu-Siemens Amilo Pa2510 (Vista) with Ubuntu-desktop-7.04-amd64 from a live-cd. It will not work!

First it says my xserver is disabled and that I should restart GDM when configured correctly. I have then manually gone through the guide after typing
sudo dpkg-reconfigure xserver-xorg. I have tried with VGA graphical driver (I have a standard VGA card) and also with VESA but neither works. 

If I then type
sudo \etc\init.d\gdm restart it says
(EE) VGA No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error
No screens found

I don't know much about this and I just tried these commandos after loking on the web.

How do I fix this?

I have a AMD64 Athlon X2 processor.

//Mats

---

### Post by jeffus_il on 2008-01-16
What graphics card do you have?

---

### Post by njparton on 2008-01-16
What specifically is a "standard VGA card"?

---

### Post by Mats_swe on 2008-01-16
It only says Standars VGA and if I type lspci I get
01:05.0 VGA compatible configuration (or maybe some other word here, I didn't write it down) [0300]: ATI Technologies Inc Unknown device [1002:791f]

Anyway. I found a driver on Fujitsus website called 
AMD 690V Chipset & X1200 ATI Graphic driver 
And in the specifications of this laptop it says:
Graphic power with the PCI graphic card
ATI Radeon™ X1200 with up to 256MB shared video
memory

So I think I must update. Should I choose Radeon then (is it available even?)?

---

### Post by jeffus_il on 2008-01-16
Yes it is available.

---

### Post by Mats_swe on 2008-01-16
Ok good. 

Another thing.

It says that I have an ACPI x86-based PC when I look in the info on my computer. Doesn't that mean that I should use the i386-installation file?
I am a bit confused, because I have AMD64.

---

### Post by jeffus_il on 2008-01-16
From this page:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

You can use either:

Standard personal computer (x86 architecture, Pentium*TM*, Celeron*TM*, Athlon*TM*, Sempron*TM*)

or:

64bit AMD and Intel computers

The 64 bit may be a little faster, but the x86 may be a little more stable.

---

### Post by mali2297 on 2008-01-16
See if this fix works for you:
[http://ubuntuforums.org/showthread.php?p=3400339](http://ubuntuforums.org/showthread.php?p=3400339)

(It concerns an x700 card instead of x1200, but it might be worth a try.)

---

### Post by Mats_swe on 2008-01-16
It didn't actuallt work to upgrade my video card. It just said that it failed...

---

### Post by jeffus_il on 2008-01-16
Use the ATI driver supplied in the linux-restricted-modules package, this is the manufacturers driver. Use the driver fglrx in your xorg configuration.

---

### Post by Mats_swe on 2008-01-16
Ok, that sounds good. Although I have no idea how to do what you just said...

Would you please explain.

---

### Post by jeffus_il on 2008-01-16
Use the Synaptic program, find in in the system menu, to install  linux-restricted-modules package if it is not installed yet.

Open a terminal.
type "sudo gedit /etc/X11/xorg.conf"

and change the line:
Device "vesa"
to:
Device "fglrx"

I haven't done this for a while and hope I didn't miss something.

---

### Post by Mats_swe on 2008-01-16
This is the situation. I haven't been able to install ubuntu at all so far, so I'm still sitting here with just Windows Vista. Can I do anything from here?

---

### Post by mali2297 on 2008-01-16
You could try 32bit Ubuntu instead, it might work out of the box.

---

### Post by Mats_swe on 2008-01-16
You mean using the file ubuntu-desktop-7.04-i386.iso ?
Or should I use the alternate CD (don't know what that's for really) ?

---

### Post by macogw on 2008-01-16
> **Mats_swe said:**
> This is the situation. I haven't been able to install ubuntu at all so far, so I'm still sitting here with just Windows Vista. Can I do anything from here?
Yes, try the Alternate install disk.  It doesn't let you play around with the live environment during install, but it should be able to install just fine.  It has a few more options available, but if you don't know what they do, it's safe to ignore them.  It uses a [text user interface](http://en.wikipedia.org/wiki/Text_user_interface) (TUI).  Once it's installed, if you still don't have any visuals when you try to use it, go to the next paragraph.

Can Ubuntu reach the internet?  If so, boot up and hit Escape when it tells you to in GRUB, then arrow down to a "recovery mode" version of Ubuntu.  It should be the 2nd one.  Recovery mode will put you at just a command line system, but with full access to everything, ok?  Please don't be scared by it.  The command line is actually fairly straightforward, like talking to the computer directly in words instead of the game of charades we normally play with them :) (I'll have to remember that analogy....that's what I get for reading Neal Stephenson's "In the Beginning Was the Command Line" :p)  Once you're in there, you can type in ```
aptitude install linux-restricted-modules
```
"aptitude" tells it to run the program aptitude, which is a program that is used for installing things (there's a program included with Ubuntu called Synaptic that lets you use checkboxes and buttons to do it).  You're telling aptitude that you want it to install a package called linux-restricted-modules.  Packages are similar to Setup.exe's in that they are for installing things on your system, but sometimes it takes a lot of them to get a program working because they depend upon each other.  That's because Linux uses what's called "shared libraries,"  meaning that instead of installing some files 10 times for 10 different programs (and using up lots of space) like Windows and OSX do, it installs them once and they share them.  Aptitude, apt-get (which is very much like an older version of aptitude--aptitude actually has a TUI like the alternate install disk if you run it by itself without any words after it), and Synaptic (which uses apt-get and aptitude to do its job--it just doesn't show you that) figure out all of that dependency stuff for you, though, so you don't have to think about it at all.  I'm just telling you so you know why it downloads more than one file when you do this.  I don't know if it will automatically send you to a another TUI to configure it or not.  If it does, just pick the fglrx driver.  If it doesn't, you can open type ```
vim /etc/X11/xorg.conf
``` Then when the file opens type ```
/Driver
``` and hit enter, which tells vim (the text editor) to search for the word driver (I think it is case-sensitive when searching).  It should take you to a line where the word "Driver" shows up.  Hit "n" (for "next") until it gets to the time that "Driver" is in a part headed ```
Section "Device"
``` There will be another word in quotes next to Driver.  That's the name of the driver it's using for your graphics.  Hit "w" (for "word") to move forward one word to the quotes around the name of the driver.  Type ci" (ok that looks weird, it's c for change, i for inside, " because that's what you want to change the inside of) and in there type "fglrx" (but don't add more quotes).  Hit Escape to get out of typing mode, then type :wq to write the changes to disk (ie save) and quit.  After restarting (by typing "reboot" at the command line), it should work.

---

### Post by Mats_swe on 2008-01-16
Ok thanks,

Right now I'm downloading the i386 cd for desktops as well as the alternate one. I will try later to see if any of them works.

But I don't really see why it would work then, because it couldn't find my video card. Won't the same problem happen again?

---

### Post by jeffus_il on 2008-01-16
Don't download the i386 version, I answered you above, it will not use your two processors, only use the x86 or 64bit iso's, OK??

---

### Post by Mats_swe on 2008-01-16
I'm sorry, I'm not really understanding what to do. These are the files I can download:

ubuntu-7.04-desktop-amd64.iso
ubuntu-7.04-desktop-i386.iso
ubuntu-7.04-alternate-amd64.iso
ubuntu-7.04-alternate-i386.iso

Which one would work on this computer?: 
[http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf]("http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf")

Except my video card won't upgrade to what it says there. On my computer it only says Standard VGA.

---

### Post by mali2297 on 2008-01-16
> **Mats_swe said:**
> I'm sorry, I'm not really understanding what to do. These are the files I can download:

ubuntu-7.04-desktop-amd64.iso
ubuntu-7.04-desktop-i386.iso
ubuntu-7.04-alternate-amd64.iso
ubuntu-7.04-alternate-i386.iso

Which one would work on this computer?: 
[http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf]("http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf")

Except my video card won't upgrade to what it says there. On my computer it only says Standard VGA.

Any *should* work. Try the suggestion given by macogw or (if you haven't tried it already) the fix I suggested.

EDIT:
By the way, why do you want to install 7.04 (Feisty) instead of 7.10 (Gutsy)?

---

### Post by Mats_swe on 2008-01-16
No reason for 7.04 really, just that I had I guide for that one.

Can I use **macogw**'s fix by just typing in the command line. I can't get into Ubuntu so I can't open the terminal in there.

---

### Post by mali2297 on 2008-01-16
> **Mats_swe said:**
> No reason for 7.04 really, just that I had I guide for that one.

Can I use **macogw**'s fix by just typing in the command line. I can't get into Ubuntu so I can't open the terminal in there.

I suggest that you download the alternate cd for Ubuntu 7.10 AMD64. After install, try first to boot normally. If it doesn't work, boot in recovery mode and use macogw's fix.

---

### Post by jeffus_il on 2008-01-16
They'll both work, don't you have one already? Just make sure you run the x86 kernel and not the 386.

> **Mats_swe said:**
> I'm sorry, I'm not really understanding what to do. These are the files I can download:

ubuntu-7.04-desktop-amd64.iso
ubuntu-7.04-desktop-i386.iso
ubuntu-7.04-alternate-amd64.iso
ubuntu-7.04-alternate-i386.iso

Which one would work on this computer?: 
[http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf](http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf)

Except my video card won't upgrade to what it says there. On my computer it only says Standard VGA.

---

### Post by Mats_swe on 2008-01-16
> **mali2297 said:**
> I suggest that you download the alternate cd for Ubuntu 7.10 AMD64. After install, try first to boot normally. If it doesn't work, boot in recovery mode and use macogw's fix.

Ok thanks. I'll download 7.10 alternate. How do I get into recovery mode? Some F-key?

---

### Post by Mats_swe on 2008-01-16
> **jeffus_il said:**
> They'll both work, don't you have one already? Just make sure you run the x86 kernel and not the 386.

How do I make this sure?

---

### Post by jeffus_il on 2008-01-16
> **Mats_swe said:**
> How do I make this sure?
Later, I just confusing you, Sorry

---

### Post by mali2297 on 2008-01-16
> **Mats_swe said:**
> Ok thanks. I'll download 7.10 alternate. How do I get into recovery mode? Some F-key?

Through the grub menu, read macogw's post.

Also, does your guide tell you to defrag Vista and shrink its partition? 
Otherwise, see here
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by macogw on 2008-01-16
> **jeffus_il said:**
> Don't download the i386 version, I answered you above, it will not use your two processors, only use the x86 or 64bit iso's, OK??

They say i386 in the iso names, but they are the "generic"-compiled kernels which can handle SMP (the thing for dual cores) just fine.

---

### Post by macogw on 2008-01-16
> **Mats_swe said:**
> Ok thanks. I'll download 7.10 alternate. How do I get into recovery mode? Some F-key?

After it's installed, when your computer turns on, it'll show the Fujitsu splash screen thing, then say something like "Loading GRUB stage 1.... Press Esc to edit" or something like that and count down.  When you press Esc, it'll bring up a menu showing a line that looks like "Ubuntu 2.6.22-14-generic" or something similar (it shows the kernel version number), then below will be one that looks with same with "(Recovery)" at the end of the line.  Just hit the down arrow to that one and hit Enter.  If you're dual-booting, Windows will be at the bottom of the list, and that's how you'd get to it in future.

For other future reference, to get to a full-screen terminal when not in recovery mode, hit ctrl+alt+F1 (or F2 or F3..  F7 should get you backr to the graphical interface, though I've noticed it's sometimes F9 instead of F7)

---

### Post by Mats_swe on 2008-01-16
> **macogw said:**
> After it's installed, when your computer turns on, it'll show the Fujitsu splash screen thing, then say something like "Loading GRUB stage 1.... Press Esc to edit" or something like that and count down.  When you press Esc, it'll bring up a menu showing a line that looks like "Ubuntu 2.6.22-14-generic" or something similar (it shows the kernel version number), then below will be one that looks with same with "(Recovery)" at the end of the line.  Just hit the down arrow to that one and hit Enter.  If you're dual-booting, Windows will be at the bottom of the list, and that's how you'd get to it in future.

For other future reference, to get to a full-screen terminal when not in recovery mode, hit ctrl+alt+F1 (or F2 or F3..  F7 should get you backr to the graphical interface, though I've noticed it's sometimes F9 instead of F7)

Ok thanks, I will try to install it with the alternate cd as soon as I can get the file downloaded. So I just have to hope that it works to install with the alternate cd. And then fix the configuration afterwards?

---

### Post by mali2297 on 2008-01-16
> **Mats_swe said:**
> Ok thanks, I will try to install it with the alternate cd as soon as I can get the file downloaded. So I just have to hope that it works to install with the alternate cd. And then fix the configuration afterwards?

Remember to try a normal boot first, the problem may not appear in Gutsy.

---

### Post by Mats_swe on 2008-01-16
> **mali2297 said:**
> Remember to try a normal boot first, the problem may not appear in Gutsy.

In Gutsy I only get to:
Running local boot scripts (\etc\rc.local)    [OK]
and then everything freezes, the cd stops working and I have to press crl-alt-del to boot into windows vista.
That was with ubuntu-7.10-desktop-amd64.iso

I have now installed the drivers for my videocard, so I have ATI Radeon Xpress 1200. With this new driver I have tried both 7.04 and 7.10 - Non of them worked!

---

### Post by porphyry75 on 2008-01-16
You're not the only one bitten by this.

I had the very same problem.  I even tried booting in Safe Graphics mode and even told it to "Continue" in the Low Resolution mode and checked "Always use mode".  Nothing worked.  I always got stuck exactly where you're getting stuck.

I downloaded it lastnight.  It was the regular 7.10 desktop.  I was able to prod it back into the window manager by logging into another terminal and typing "sudo gdm".  Then the really horrid thing is it was still the crappy resolution so I had to move my panels around to actually be able to hit the "Continue" button!  I could enable the restricted driver in this mode... but it requires a restart so it gets lost!

To make matters worse, when I got to the partitioner it threw an error saying it couldn't initialize the fs on my sda device!  That pretty much freaked me right out so I ditched the install.

I noticed some pretty interesting errors concerning gdm, which I believe were in /var/log/syslog.  You might wanna tail /var/log/syslog and /var/log/messages and just post the last 5 lines or so of each when you get hung up.

"sudo tail -n 10 /var/log/messages"
"sudo tail -n 10 /var/log/syslog"


The funny thing is Kubuntu 7.04 installed just fine on it, then I upgraded to Kubuntu 7.10 using adept.  So I don't know if a direct install of Kubuntu 7.10 will cause the same error.  I think I might giver it a go and see.

Not to blow my own horn here, but I don't consider myself a beginner and I ended up throwing my hands up in the air lastnight and giving up.  So don't feel bad :)

Here's a brief rundown of what I have.  

macross@porphyry:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I'm currently running Kubuntu 7.10 but I'd like to start fresh and do a reinstall of Ubuntu cuz it's been awhile.

---

### Post by porphyry75 on 2008-01-16
Also:

macross@porphyry:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD1600JS-60N Rev: 10.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05

macross@porphyry:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by Mats_swe on 2008-01-16
Kubuntu, hmm. Maybe I should try that. Why do you want to change to Ubuntu. What are the restrictions on Kubuntu?

---

### Post by porphyry75 on 2008-01-16
Kubuntu is the same as Ubuntu but uses KDE instead.  Every so often I just feel like a change so I kinda alternate between the 2 desktops.  I've recently been hankering for Gnome and I'm currently runnin KDE 3.5, KDE4 and Gnome on the same distro.  I wanna switch to just one.

You can try Kubuntu 7.10.  I'd be interested to know whether their plain 7.10 desktop install CD works for you.  If it does then it could be a problem with GDM or the Gnome installer.

---

### Post by zipperback on 2008-01-16
> **njparton said:**
> What specifically is a "standard VGA card"?

[http://en.wikipedia.org/wiki/Video_Graphics_Array](http://en.wikipedia.org/wiki/Video_Graphics_Array)

zipperback
:popcorn:

---

### Post by Mats_swe on 2008-01-16
A question:
Do I have to burn the image file to a CD or can I as well use a DVD without problems?

---

### Post by zipperback on 2008-01-16
> **Mats_swe said:**
> Kubuntu, hmm. Maybe I should try that. Why do you want to change to Ubuntu. What are the restrictions on Kubuntu?



The difference is Ubuntu uses the Gnome Desktop, Kubuntu uses the KDE Desktop.

You can run KDE applications if you have Ubuntu installed, I have several kde applications I use on a nearly daily basis. Use synaptic to install the applications and the required dependencies will be installed with them.

- zipperback
:popcorn:

---

### Post by porphyry75 on 2008-01-16
Here's the same bug in a different thread.

[http://ubuntuforums.org/showthread.php?t=579393](http://ubuntuforums.org/showthread.php?t=579393)

This is pretty bad... they cannot get Kubuntu 7.10 to install on this hardware either.

I might need to hold off upgrading for quite awhile.

---

### Post by porphyry75 on 2008-01-16
Also [http://ubuntuforums.org/showthread.php?t=617352](http://ubuntuforums.org/showthread.php?t=617352)

---

### Post by porphyry75 on 2008-01-16
Yey.!

I found these directions somewhere on the web but I don't remember where:

When it fails to load the screen and presents you with a dialog, bang on the Alt-F2 to bring up a terminal.  Then type:

sudo apt-get install xorg-driver-fglrx
startx

It should start up in the right resolution and let you go further.  If it brings you out of X then keep banging on ALT-F7.

Once you've installed and rebooted yer gonna need to do the same thing to get into X the first time.  Once you're in X enable the restricted driver and reboot.

Apparently changing the resolution is something that you can only do by editing the xorg.conf and restarting X.  I haven't gotten there yet but I'm used to this cuz I had to do this with 7.04 as well.

:guitar:

---

### Post by Mats_swe on 2008-01-17
I am trying to install with 7.10 alternate. I just get stuck on the partitioning part. I have C (Vista) and D (Other stuff) and an empty logical unit F that I created. Now, how do I install Ubuntu on that one. Must it be a primary partition (not a logical unit) to install on?

---

### Post by mali2297 on 2008-01-17
> **Mats_swe said:**
> I am trying to install with 7.10 alternate. I just get stuck on the partitioning part. I have C (Vista) and D (Other stuff) and an empty logical unit F that I created. Now, how do I install Ubuntu on that one. Must it be a primary partition (not a logical unit) to install on?

This [guide]("http://users.bigpond.net.au/hermanzone/p3.htm") might help. Basically, you need a root partition / and, in addition, a small swap partition.

---

### Post by Mats_swe on 2008-01-17
This is my situation now:

I have installed Ubuntu 7.10 with the alternate cd. If I try to boot into ubuntu it stops at 
Running local boot scripts (\etc\rc.local)

If I type
sudo nano (or vim) \etc\X11\xorg.conf I just see a blank file!

If I try
sudo dpkg-reconfigure xserver-xorg I can't choose fglrx (which you told me to use).

If I do
sudo aptitude install linux-restricted-modules
something is installed

If I do
sudo apt-get install xorg-driver-fglrx
it complains that it doesn't work.

Any suggestions?

---

### Post by mali2297 on 2008-01-17
> **Mats_swe said:**
> 
If I type
sudo nano (or vim) \etc\X11\xorg.conf I just see a blank file!

It's **/etc/X11/xorg.conf** ("/" instead of "\").

> 
If I try
sudo dpkg-reconfigure xserver-xorg I can't choose fglrx (which you told me to use).

If I do
sudo aptitude install linux-restricted-modules
something is installed

Then try **dpkg-reconfigure xserver-xorg** again and see if you find fglrx. [COLOR="green"]&#8592; Try this first.[/COLOR]

> 
If I do
sudo apt-get install xorg-driver-fglrx
it complains that it doesn't work.

Open sources.list:
```

sudo nano -B /etc/apt/sources.list

```
and check that there is no # in front of a line similar to
```

deb http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted

```
If so, remove #, save (ctrl+o) and quit (ctrl+x). Then run
```

sudo apt-get update
sudo apt-get install xorg-driver-fglrx

```

---

### Post by Mats_swe on 2008-01-17
It didn't work. There was no # in front of that.

---

### Post by mali2297 on 2008-01-18
> **Mats_swe said:**
> It didn't work. There was no # in front of that.

Can you give us more information about the errors?
For example, post the error message that you get when you run
```

sudo apt-get install xorg-driver-fglrx

```

Also, did you try changing **ati** with **radeon** in xorg.conf? (This [tip]("http://ubuntuforums.org/showthread.php?p=3400339").)

---

### Post by Mats_swe on 2008-01-18
It finally worked:

[http://ubuntuforums.org/showthread.php?p=4161343#post4161343](http://ubuntuforums.org/showthread.php?p=4161343#post4161343)

---

