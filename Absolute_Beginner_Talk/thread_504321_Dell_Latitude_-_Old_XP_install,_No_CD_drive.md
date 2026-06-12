---
title: "Dell Latitude - Old XP install, No CD drive"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by geoffcj on 2007-07-19
I was given an Older (2001) Dell Latitude LS laptop. I've been using Ubuntu on a desktop PC for awhile, and I really like it, and like the idea of Open Source. I have another Dell Laptop with Windows on it, that I use for Photoshop and Illustrator, but I like the idea of having a Linux laptop, and the small size of the Latitude is ideal.

So here's the issue, the LS doesn't have a CD drive, and I don't own a external CD drive. The LS has XP on it, but I don't have any of the passwords to login to windows, so I can't login and download it to the hardrive.

Things I do have -
External Hard Drive (USB)
External CD Drive 
Ubuntu CD
USB Card reader with a 2 GB card.
1 GB Thumb Drive
A wireless card and connection
A hard wire network connection
A linux PC online
An XP laptop


Can I load Linux onto one of those, and install from there? How? As much detail as possible is appreciated. I'm not a high level user, am I asking for trouble installing linux on a laptop? Is there a way to force this machine to recognize the CD drive without being in windows? 

Thanks for the help,
Geoff

---

### Post by wolfen69 on 2007-07-19
you can boot to the external cd drive for your laptop.

---

### Post by meborc on 2007-07-19
hmm you said > ...and I don't own a external CD drive...and then listed this> Things I do have -
External Hard Drive (USB)
External CD Drive 
Ubuntu CD
...

if you DO have a external CD drive then you are set :D ... if you don't... welll what i would do is to buy a ide-usb cable... take out my cd drive from my desktop and hook it up with the laptop... ide-usb cable is always a good thing to own... if you need to save data from old HDD's for example...

you probably could also install from a usb stick... i'll check the wiki...

EDIT - this is the link to how to install from usb stick [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ... this is reported to work for feisty... so good luck :D

---

### Post by geoffcj on 2007-07-19
Sorry, I'd copied that from something I wrote earlier, and modified it. 

I have borrowed a USB cd drive, but can't get it to boot from the USB drive.  Couple things I've googled said this machine won't boot from a USB drive, and I've tried using f8 then changing the order, and it continues to boot to windows. 

Ugh. 

Thanks for any hints. 

Geoff

---

### Post by meborc on 2007-07-19
does it have a floppy device? or is it ment to be used with a dock? maybe you can get the dock for a couple of euros of ebay?... fishing wide here :)

---

### Post by geoffcj on 2007-07-19
yeah.  No floppy with it.  

I was hopeing for some clever network based solution. => 

Geoff

---

### Post by meborc on 2007-07-19
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

found these two... i have no idea if they will work... but still... since you have free time ;)

---

### Post by djchandler on 2007-07-19
> **geoffcj said:**
> Sorry, I'd copied that from something I wrote earlier, and modified it. 

I have borrowed a USB cd drive, but can't get it to boot from the USB drive.  Couple things I've googled said this machine won't boot from a USB drive, and I've tried using f8 then changing the order, and it continues to boot to windows. 

Ugh. 

Thanks for any hints. 

Geoff

One thing I believe you need to do is to use DBAN to erase the hard disk drive in the laptop, which can be run from a floppy. Is there a floppy drive built into the laptop? Also, it may be possible to boot a linux kernel from the floppy and mount an external USB device and run the installer after mounting the external device.

When you turn the laptop on, isn't there a sign-on message that tells you what key(s) to push to enter configuration? Somebody with more Linux experience than me needs to get into this thread, because the only Linux bootable floppy I know about is on the DBAN floppy. I'm stepping out of this now to watch this thread. There must be a way to boot something else besides the internal hard drive.

DJ

PS Give us more information about the laptop so we can figure out what you have. Can you tell us the processor at least, or a model # in addition to the LS designation?

---

### Post by geoffcj on 2007-07-19
wow.  That's kind of greek to me.  I guess I won't go Linux on a laptop yet, since I'm not quite willing to F* with my other Dell yet...still learning. 

Geoff

---

### Post by ubanchaos on 2007-07-19
get an external that works with xp first and if u cant login u need to restart and hit f8 and go to safe mode and log on as the administrater and go delete the other password protected accout and restart

---

### Post by geoffcj on 2007-07-19
I can get into the setup menu, but there is no floppy, nor a CD drive.   I have a USB CD drive, but even getting into the setup, or the boot menu, I can't make it recognize and boot from the USB drive. 

The computer was given to me, and I don't have admin access.  Don't know the Admin passwords.  I can get into XP, but only with a Limited user account.  

I'm willing to battle, but I'm starting to wonder if there is a point. 

The Model is Dell Latitude LS, Model # PP01S

---

### Post by geoffcj on 2007-07-19
> **ubanchaos said:**
> get an external that works with xp first and if u cant login u need to restart and hit f8 and go to safe mode and log on as the administrater and go delete the other password protected accout and restart

Yeah.  I can't figure out how to get on as an adminsrator.

---

### Post by djchandler on 2007-07-19
> **geoffcj said:**
> Yeah.  I can't figure out how to get on as an adminsrator.

This laptop is probably a Pentium III 400 mhz. How much are you willing to invest in this? There are parts galore  if you google your model--tons of ebay listings, and so far off Dell's radar I still haven't found a solid link for it on their website through Google. And you will pay too much for its parts, no matter what you find. It sounds like a doorstop to me, not worth your trouble if you have another computer. When you get a floppy or cd drive for it that fits inside it, not usb, we may be able to help you then. I don't want to sound mean, but I'm out of this thread. This  is my last post in this thread until you find the parts you need. You can send me a private message when you have the hardware necessary, and I'll be glad to help. It's an unsolvable conundrum as far as I can tell until you come up with the missing hardware. The motherboard will never support USB booting.

One more thing. All the external media devices (floppy drive, cd drive) for this model appear to be connected by a special cable that connects to the back of the computer. The USB port is on the side. Do you even have the proprietary cable that allows you to connect external media devices to the back of the computer? That is what is going to be hard to find, and you will pay plenty for it is my guess.  :confused:

Does the attached drawing look familiar?
[ATTACH]38644[/ATTACH]
DJ

---

