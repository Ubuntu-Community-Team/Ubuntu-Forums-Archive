---
title: "Linksys wpc54gs ver2 Dilemma"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-05-27
Got a slight problem here.  I can't get to Internet with my laptop that I've installed Ubuntu on, not far enough along to do so.   At this moment, I'm typing on a Windows based system and need to get copies of various things to bring into the Ubuntu machine via a thumb drive.

What would be the best way to go about this and what different files am I likely to need?  

Browning>>>

---

### Post by medley on 2007-05-27
> **tgbrowning said:**
> Got a slight problem here.  I can't get to Internet with my laptop that I've installed Ubuntu on, not far enough along to do so.   At this moment, I'm typing on a Windows based system and need to get copies of various things to bring into the Ubuntu machine via a thumb drive.

What would be the best way to go about this and what different files am I likely to need?  

Browning>>>

You'll probably need to use ndiswrapper with your windows driver for that card. I wrestled with the usb one for a few days. I would suggest downloading the latest version of ndiswrapper; the one the I got from the repositories didn't work for me. I know this all can be intimidating but it's the way you learn how to use Linux. I've been using Kubuntu for about 6 months now, and have cursed alot, but have also learned alot, and can usually figure things out eventually.

Good luck.

---

### Post by ElEdwards on 2007-05-27
I have the WPC54G card and found that if I plugged it in and THEN turned on my laptop and booted Ubuntu, it recognized the card with no trouble.  I didn't have to install anything else and I'm using it now as I type this.

---

### Post by tgbrowning on 2007-05-28
Gave it a shot. It sees the card is there, and says it's wireless, but it's alias is eth1, which is wrong. 

Checked the device manager and it shows the card there, but when you get down the specific card, below the PCI controller bus stuff (correctly IDed by the way), it's listed as an unknown device.

It will "activate" supposedly, but there's no response whatsoever.  

Thanks for the try.  

Browning>>>

---

### Post by medley on 2007-05-28
> **tgbrowning said:**
> Gave it a shot. It sees the card is there, and says it's wireless, but it's alias is eth1, which is wrong. 

Checked the device manager and it shows the card there, but when you get down the specific card, below the PCI controller bus stuff (correctly IDed by the way), it's listed as an unknown device.

It will "activate" supposedly, but there's no response whatsoever.  

Thanks for the try.  

Browning>>>

In the terminal, if you type 'iwconfig', what do you get? If sounds to me like you don't have a driver installed for the card. As I mentioned previously, you may very well have to use ndiswrapper. It allows you to use a windows driver in Linux, and works very well. I'm using it on one of my Linux systems (wireless).

---

### Post by tgbrowning on 2007-05-28
> **medley said:**
> You'll probably need to use ndiswrapper with your windows driver for that card. I wrestled with the usb one for a few days. I would suggest downloading the latest version of ndiswrapper; the one the I got from the repositories didn't work for me. I know this all can be intimidating but it's the way you learn how to use Linux. I've been using Kubuntu for about 6 months now, and have cursed alot, but have also learned alot, and can usually figure things out eventually.

Good luck.

Oh, I'm only a tiny bit frustrated. But am a bit befuddled because I'm having a dickens of a time finding stuff.  The book I bought said I'm supposed to have a C/C++ compiler but I'll be damned if I can find it. I can't recognize which files are executables and which are merely documents/text files.  Here's what I've got so far:


F5D7010-v2.4.4.exe
ndiswrapper-1.44.tar.gz
wmp54g_driver_utility_v1.2.zip
wmp54g_driver_utility_v1.3.zip

all from Linksys, but I have no idea which file has what I want in it.  The darned .tar.gz is all the source code for ndiswrapper but I have no idea if I'm supposed to run it through the compiler (that I can't find) to get it.

I'd kind of like to download the bloody binary file that I need and just go from there, but it doesn't look like I'm going to be able to do that tonight.  

rats.

Browning>>>

---

### Post by medley on 2007-05-28
> **tgbrowning said:**
> Oh, I'm only a tiny bit frustrated. But am a bit befuddled because I'm having a dickens of a time finding stuff.  The book I bought said I'm supposed to have a C/C++ compiler but I'll be damned if I can find it. I can't recognize which files are executables and which are merely documents/text files.  Here's what I've got so far:


F5D7010-v2.4.4.exe
ndiswrapper-1.44.tar.gz
wmp54g_driver_utility_v1.2.zip
wmp54g_driver_utility_v1.3.zip

all from Linksys, but I have no idea which file has what I want in it.  The darned .tar.gz is all the source code for ndiswrapper but I have no idea if I'm supposed to run it through the compiler (that I can't find) to get it.

I'd kind of like to download the bloody binary file that I need and just go from there, but it doesn't look like I'm going to be able to do that tonight.  

rats.

Browning>>>

You can find a version of ndiswrapper in your default repositories (using apt), or you can compile it yourself. That's what I ended up doing, and while it sounds intimidating, it's pretty straightforward.

Start apt and search for 'build-essential'. It will install most of the compiler type stuff you'll need. Then extract the ndiswrapper tarball into a directory that you'll be able to find from the terminal. You should be able to do this from your desktop by right clicking the file; you should see an option to extract the file. Then go into that directory in terminal, and type 'make'. Watch for any dependencies that aren't met (ie files are missing) and install those from apt and try make again.

I found a pretty good walkthrough that I'll see if I can find. Try the above in the meantime.

Phil

---

### Post by medley on 2007-05-28
> **tgbrowning said:**
> Oh, I'm only a tiny bit frustrated. But am a bit befuddled because I'm having a dickens of a time finding stuff.  The book I bought said I'm supposed to have a C/C++ compiler but I'll be damned if I can find it. I can't recognize which files are executables and which are merely documents/text files.  Here's what I've got so far:


F5D7010-v2.4.4.exe
ndiswrapper-1.44.tar.gz
wmp54g_driver_utility_v1.2.zip
wmp54g_driver_utility_v1.3.zip

all from Linksys, but I have no idea which file has what I want in it.  The darned .tar.gz is all the source code for ndiswrapper but I have no idea if I'm supposed to run it through the compiler (that I can't find) to get it.

I'd kind of like to download the bloody binary file that I need and just go from there, but it doesn't look like I'm going to be able to do that tonight.  

rats.

Browning>>>

I found this walkthrough very helpful. It's for the USB version of that adapter, but it should guide you through compiling ndiswapper and hopefully getting your card working.

[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GS](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GS)

Good luck.

---

