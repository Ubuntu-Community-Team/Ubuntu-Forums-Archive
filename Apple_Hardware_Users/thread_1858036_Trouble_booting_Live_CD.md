---
title: "Trouble booting Live CD"
date: 2011-10-11
forum: Apple Hardware Users
---

### Post by Christoph Trusch on 2011-10-11
Hello, 

I want to try the Ubuntu 11.10 live CD for PPC Macs ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)). I use a Pismo PowerBook G3 400MHz with 768 MB RAM that is currently running Mac OS X 10.4.11. Since this version of OS X is the end of the road for the machine, I'm looking at my options to keep the computer useful.

Burned the iso image to DVD, started up, kernel seems to be loading. I end up with a screen that reads 

"BusyBox […] (initramfs)"

…obviously waiting for a command. Typing 'help' doesn't help because I have no idea which of the commands to use or what they do. It seems to be a functional command line, though, since typing 'reboot' does reboot the computer. 

I'm at a loss and I was unable to find an explanation on the Ubuntu website ([https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)). All instructions seem to presume that some sort of GUI screen has already loaded when booting the live CD/DVD.


[[IMG]http://s1.postimage.org/fjzsffwi8/IMG_0203.jpg[/IMG]]("http://www.postimage.org/")

---

### Post by rsavage on 2011-10-11
You don't want to install ubuntu 11.10 on that machine.  It will be too slow I should imagine.  Also 11.10 is still in development.  I'd encourage you to install lubuntu or xubuntu.  See [http://ubuntuforums.org/showpost.php?p=11285107&postcount=198](http://ubuntuforums.org/showpost.php?p=11285107&postcount=198) from the powerpc sticky thread.

---

### Post by Christoph Trusch on 2011-10-11
Thanks for your answer. Is there a live CD for lubuntu or xubuntu? Right now I don't want to install anything on this machine, I'd like to try and see first if Ubuntu or any Linux is for me. My last Linux experience dates back to 2003 (KDE). 

But you're right, maybe I shouldn't start with a nightly build. I'll try the Ubuntu Live CD for 10.04 tomorrow (which I understand is the stable version), and see if this boots up on the Pismo PowerBook. I also have a 1.3 GHz G4 PowerBook to try which should be fast enough for any consumer OS that's intended to run on this hardware platform.

---

### Post by Christoph Trusch on 2011-10-12
The Ubuntu 10.04 live CD works as expected, even with the correct Wifi card, ADB trackpad and sound card drivers out of the box. Impressive. There are some glitches such as monitor resolution (too low and only occupying the first 800x600 pixels of the display), and only Firefox 3.6, but I'll get back to that when I'm actually ready to install.

If there are Live CDs available for the other distributions I'd like to try them out as well.

---

### Post by rsavage on 2011-10-12
xubuntu 10.04 [http://cdimage.ubuntu.com/xubuntu/ports/releases/lucid/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/lucid/release/) .  It's more resource hungry than 11.04 I think.
 
There is a lubuntu cd in testing for 11.10.  See the last few pages of the powerpc sticky thread.  It used to work, don't know about now.
 
Never found using cds very satisfying.  Way too slow.  If you burn it to a a usb drive it is much better and more like the real thing.
 
Your resolution problems can be fixed.

---

### Post by Christoph Trusch on 2011-10-12
I don't care too much for speed – this is a 400 MHz G3, there's no modern OS that will run exceptionally fast on this machine. 

Downloading the Xubuntu and Lubuntu images…

Having read through the forum a bit, I'm a bit scared by all the workarounds that might have to be done to get a useful Linux system on PPC. Being an exclusive OS X user for almost 10 years I'm certainly spoiled by the system integration.  

I own three PPC Macs (iBook G3 800 MHz, PowerBook G3 400 MHz, PowerBook G4 1333 MHz), and my options right now are:

- Try Linux Mint or Ubuntu/Xubuntu/Lubuntu to stay current. 
- Milk OS X (10.4 on the G3s and 10.5 on the G4) for what it's worth and stay there as long as possible. TenFourFox (Firefox 7 for PPC Macs) definitely helps by providing a current browser with effective JS acceleration, and 10.5 ist still almost up to date.
- Buy an Intel Mac.

I still haven't made up my mind.

---

### Post by rsavage on 2011-10-12
> **Christoph Trusch said:**
> I don't care too much for speed – this is a 400 MHz G3, there's no modern OS that will run exceptionally fast on this machine. 
 
I think you'd be surprised by lubuntu. When I reduce the processor speed of my ibook to 600MHz I can't say I notice a dramatic reduction in speed.
 
 
> **Christoph Trusch said:**
> Downloading the Xubuntu and Lubuntu images…
 
Having read through the forum a bit, I'm a bit scared by all the workarounds that might have to be done to get a useful Linux system on PPC. 
The only things you haven't got on PPC is adobe flash and chrome browser. People run into difficulty when a) they don't follow instructions b) follow random instructions that they've found on google or c) try to do overcomplicated stuff. If you are referring to the lubuntu thread I wrote then yes it is long because I tried to include every problem people could have! But, honestly, I don't think there is anything complicated there. Don't be freaked out because you are going to have to type something in a terminal. Once you are up and running ubuntu/xubuntu/lubuntu is very easy to use.
 
> **Christoph Trusch said:**
> Being an exclusive OS X user for almost 10 years I'm certainly spoiled by the system integration. 
 
I own three PPC Macs (iBook G3 800 MHz, PowerBook G3 400 MHz, PowerBook G4 1333 MHz), and my options right now are:
 
- Try Linux Mint or Ubuntu/Xubuntu/Lubuntu to stay current. 
- Milk OS X (10.4 on the G3s and 10.5 on the G4) for what it's worth and stay there as long as possible. TenFourFox (Firefox 7 for PPC Macs) definitely helps by providing a current browser with effective JS acceleration, and 10.5 ist still almost up to date.
- Buy an Intel Mac.
 
I still haven't made up my mind. 
Well an intel mac costs money and ubuntu is free so what have you got to lose by trying it?

---

### Post by Christoph Trusch on 2011-10-12
> ubuntu is free so what have you got to lose by trying it
That's why I'm here :-)

Hm… the Lubuntu 11.10 live CD ends up at the same (initramfs) prompt as the nightly Ubuntu live CD I tried first. The Xubuntu CD (DVD, really,  because it's 744 MB) isn't even recognized as a valid boot device. Not promising… So  I'll stick to Ubuntu 10.04 for the time being.

>  I think you'd be surprised by lubuntu. 
Well, the 400 MHz G3 is capable to run 10.4.11 very decently, the only limitation being the 8 MB video card which is really outdated. I think the GUI is almost always speedy enough, it's the more complicated things that require processing power such as transcoding video or applying filters in image editing software. I can wait, the point is whether I'll be able to run modern software at all which is going downhill right now on OS X 10.4.

> 
Don't be freaked out because you are going to have to type something in a terminal. 
OS X has a terminal, too, and a single user mode :-) Only I don't use it for simple things like renaming files or anything that can be done in the GUI. Checking the file system in Single User Mode before making backups is my standard procedure. So I'm not afraid.

Is it generally possible to install Ubuntu on an external Firewire HD? Because I see now that the live CDs won't get me that far and I'd really like to try it for real. But without destroying the OS 9/OS X installations on the internal HD before I'm ready to make the switch. I need this PowerBook for testing OS 9/Classilla for the foreseeable future.

---

### Post by rsavage on 2011-10-12
> **Christoph Trusch said:**
> I think the GUI is almost always speedy enough, it's the more complicated things that require processing power such as transcoding video or applying filters in image editing software. 
 
Yeah, you are always limited by the capabilities of the hardware!
 
> **Christoph Trusch said:**
> Is it generally possible to install Ubuntu on an external Firewire HD? Because I see now that the live CDs won't get me that far and I'd really like to try it for real. But without destroying the OS 9/OS X installations on the internal HD before I'm ready to make the switch. I need this PowerBook for testing OS 9/Classilla for the foreseeable future. 
 
Should be possible, don't think I've read of anyone doing it though (but that doesn't mean anything). Firewire is bootable right? I know people install it on a usb drive, but then you have to adjust some things to get it to boot automatically.

---

### Post by rsavage on 2011-10-12
Bit old, but firewire works [http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

---

