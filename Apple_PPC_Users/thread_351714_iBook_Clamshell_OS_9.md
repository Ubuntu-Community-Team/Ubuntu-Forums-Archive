---
title: "iBook Clamshell OS 9"
date: 2007-02-02
forum: Apple PPC Users
---

### Post by Lotus Blossom on 2007-02-02
I have put Ubuntu 6.10 onto a CD using an ISO recorder and I have inserted the CD into my clamshell in hopes of changing the OS from the now current Mac OS 9.2. I opened the CD and opened the install folder, then clicked "ofboot.b"

A window popped up saying, "Document "ofboot.b" could not be opened because the application program that created it could not be found."

Below that in a smaller text is said, "Could not find a translation extension for appropriate translators."

Does anyone know what I have done wrong? I think something could have gone wrong when putting Ubuntu onto the CD... it went all the way to 100%, then it said, "insert writable media into drive E and press OK to continue or cancel to stop."

I was confused since I had that CD in drive E...

Hm... any suggestions or advice?

I followed these directions mainly:
[http://forums.macnn.com/66/ibook-and-macbook/316137/the-ibook-clamshell-os-best-you/](http://forums.macnn.com/66/ibook-and-macbook/316137/the-ibook-clamshell-os-best-you/)

Go [here.]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease")

Click "North America" (or whatever country you live in) under "Ubuntu 6.10, the newest release". Click on your country. Find a mirror from the list that is close to where you live - it can make a difference in download speeds. Click the mirror and download the "CD Image for Apple Macintosh". Download the ISO and burn it in Disk Utility.

If you're burning on a Windows machine, download [Alex Feinman's ISO Recorder PowerToy]("http://isorecorder.alexfeinman.com/isorecorder.htm") and install it. You can then right-click on the ISO and hit "copy to CD".

Boot off the CD (Option+Boot or C+Boot). When Ubuntu is finished booting, there should be an icon on the desktop of Ubuntu to install to a hard drive. I don't know why, but I was never able to install to my clamshell - it got 90% done and then failed, rolled back the installation, and I was too impatient to try it again. Just a sidenote.

Make sure your drive is already partitioned and ready to go. If you want to dual-boot, it's a good idea to install OS X or OS 9 first on the first partition. Ubuntu goes on the second partition, and you should have a third partition available for the two to read/write to in order to share files. I'd recommend formatting in FAT32 - it's the most universal format and will allow sharing between Linux, UNIX, a Mac OS (I'm assuming OS 9 supports FAT32 read/write), and Windows.

Good luck! Use the forums at ubuntu.com if you have problems.

---

### Post by linear on 2007-02-02
Did you copy the .iso file to the CD (won't get you a bootable disk) or did you burn the .iso as an image to the CD (this is the way to do it)?

Once the CD is burned correctly, you need to boot the computer from it - insert the CD, and then hold down the "c" key while re-booting. (Or hold down the "option" key and select the Linux disk from the graphical boot menu.)

---

### Post by Lotus Blossom on 2007-02-02
Oh okay, thanks for the clarifications... I'm.. I'm terrible at all this.. *sigh*

Anyway, so I got everything to work properly, everything was going smoothly, and then this came up:

[IMG]http://i19.tinypic.com/2jdj52v.jpg[/IMG]

At the top it says, "Please remove the disc, close the tray (if any), and press ENTER to continue," so I did all that and... nothing happened... and the screen has stayed like that since...

*sigh*

---

### Post by pauljwells on 2007-02-02
Nice picture ;)

I don't think this is a problem. It looks like the install has finished and you need to reboot the machine to get it to start up in ubuntu. It *should* have rebooted itself, but wth some configs ubuntu has trouble actually switching the machine off.

Just hold down the power button to switch it off, press it again to start it up and you should get the 'yaboot' screen asking if you want to boot os9 (if you kept it) or ubuntu.

Good luck. Your fun is just begining...

---

### Post by Gen2ly on 2007-02-03
I recently installed Ubuntu on my iBook, works like a dream.  Like to know how it went.

---

