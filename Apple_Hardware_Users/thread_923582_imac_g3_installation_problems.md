---
title: "imac g3 installation problems"
date: 2008-09-18
forum: Apple Hardware Users
---

### Post by Lowcountry on 2008-09-18
I recently aquired an old imac g3 from a craiglist seller.  I was told everything was working fine, but when I got it home, the cd drive didn't work.  Long story short, the seller turned out to be an a-hole, and since I was already out $50, I figured I'd shell out another $20 on a new cd drive.
The new drive came in today, and it works fine.
I tried to boot the xubuntu cd by holding down the "c" key at startup.  Nothing happened, the os just booted.
Next, I burned ubuntu 8.04.1 powerpc, and that didn't start up either.
Now, when the computer is booted, I get the flashing question mark.
I've searched and I've done the reset by holding down cmd, option, p, r, but I'm still SOL.
Any suggeestions?
I'm about to face defeat and throw it in the garbage, but I REALLY want it to work.
Thanks!

---

### Post by tiresia on 2008-09-18
Do you own a MacOS Installer? You could try with it, just to understand if your new cd drive works - I mean if you can boot from it

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> Do you own a MacOS Installer? You could try with it, just to understand if your new cd drive works - I mean if you can boot from it

No, this is my first mac, and it came with nothing.  When I put in the new cd drive earlier today, and when the os was working, I put in a cd with pictures on it and it opened it.

EDIT--Thanks though.
Also, there was only one cord bundle to plug in, is that right?

---

### Post by tiresia on 2008-09-18
Where did you find the Ubuntu CD Installer? And how did you burn it?
Which OS is now installed on your Mac? MacOS9?

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> Where did you find the Ubuntu CD Installer? And how did you burn it?
Which OS is now installed on your Mac? MacOS9?
I downloaded the alternate installer from [http://cdimage.ubuntu.com/ports/releases/hardy/release/]("http://cdimage.ubuntu.com/ports/releases/hardy/release/")
I burned in in windows at 4x.
I also tried xubuntu--which I believe doesn't have a seperate powerpc download.
MacOS9.2 is what was on it.
When I boot up and hold c, I hear the cd spinning, but after about 10 sec., the flashing question mark appears.

---

### Post by tiresia on 2008-09-18
> **Lowcountry said:**
> 
I burned in in windows at 4x.

MacOS9.2 is what was on it.
When I boot up and hold c, I hear the cd spinning, but after about 10 sec., the flashing question mark appears.

Ok, most probably the CD is not in the right format. Which program did you use in Win? Do you have also Linux installed on your PC? Can you burn with your CD Drive in MacOS9, or you can just read CD?
Last question: are you burning on CD, that your optical drive support (CD-R or CD+R)?

---

### Post by Bikerbob on 2008-09-18
> **Lowcountry said:**
> I figured I'd shell out another $20 on a new cd drive.
The new drive came in today, and it works fine.
I tried to boot the xubuntu cd by holding down the "c" key at startup.  Nothing happened, the os just booted.
Next, I burned ubuntu 8.04.1 powerpc, and that didn't start up either.
Now, when the computer is booted, I get the flashing question mark.
I've searched and I've done the reset by holding down cmd, option, p, r, but I'm still SOL.
Any suggeestions?

Lowcountry - the cd you bought.. are we talking joe cd drive from a computer store? If so that could be a problem as most older macs are very picky about the apple cd drive to boot from.

Now you are saying after trying to get it to boot with the cd that you cannot get it to see your original boot partition? and that it now is only coming up with a question mark?

start up and hold 'd'  this forces it to use your first HD.

you can also try and reset the NV ram as well.. I know you have done the pram.. but maybe you need to do the NV

that is cmd opt n v

Do you still have the CD in when you get the question mark?

check here  [http://davespicks.com/writing/programming/mackeys.html](http://davespicks.com/writing/programming/mackeys.html)

This gives a very nice list of key commands to use on the mac.

James

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> Ok, most probably the CD is not in the right format. Which program did you use in Win? Do you have also Linux installed on your PC? Can you burn with your CD Drive in MacOS9, or you can just read CD?
Last question: are you burning on CD, that your optical drive support (CD-R or CD+R)?

I burned the cd using windows.  I used iso recorder.  This is the way I've done it in the past for pcs that I have Ubuntu on.  This is just my first experience with a mac.
The cd I used was a Maxell cd-r.

---

### Post by Lowcountry on 2008-09-18
> **Bikerbob said:**
> Lowcountry - the cd you bought.. are we talking joe cd drive from a computer store? If so that could be a problem as most older macs are very picky about the apple cd drive to boot from.

Now you are saying after trying to get it to boot with the cd that you cannot get it to see your original boot partition? and that it now is only coming up with a question mark?

start up and hold 'd'  this forces it to use your first HD.

you can also try and reset the NV ram as well.. I know you have done the pram.. but maybe you need to do the NV

that is cmd opt n v

Do you still have the CD in when you get the question mark?

check here  [http://davespicks.com/writing/programming/mackeys.html](http://davespicks.com/writing/programming/mackeys.html)

This gives a very nice list of key commands to use on the mac.

James

I bought a replacement tray loading cd drive.  I assume it was salvaged out of another imac g3.
I'll give some of those commands a try.

Thanks for helping.

---

### Post by tiresia on 2008-09-18
If you can also burn CD with your new optical drive, you can try to burn the ubuntu iso-image using the Apple Disk Utility (Disk Copy) you have in MacOS9.

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> If you can also burn CD with your new optical drive, you can try to burn the ubuntu iso-image using the Apple Disk Utility (Disk Copy) you have in MacOS9.

MacOS9 won't boot up anymore...All I get is the flashing question mark.:(

---

### Post by tiresia on 2008-09-18
Start your iMac again and press Command+Option+O+F to get to Open Firmware.
At the prompt type

```
0 > reset-nvram
```
Press Return
```
0 > reset-all

```Press Return

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> Start your iMac again and press Command+Option+O+F to get to Open Firmware.
At the prompt type

```
0 > reset-nvram
```
Press Return
```
0 > reset-all

```Press Return

Thanks for hanging in there with me.  I did everything you just said, but after pressing return after the second command, I still get the flashing question mark.

---

### Post by tiresia on 2008-09-18
When you are in Open Firmware, if you type 'printenv' which value do you get for 'boot'?

---

### Post by tiresia on 2008-09-18
If you do not yet get MacOS9, try again this commands (with set-defaults too)

```
reset-nvram
set-defaults
reset-all
```

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> When you are in Open Firmware, if you type 'printenv' which value do you get for 'boot'?

auto-boot?   true   true
boot-device   (blank)   (blank)
boot-file   (blank)   (blank)
boot-command   mac-boot   mac-boot
forced-boot   (blank)   (blank)

There isn't one that just says boot

---

### Post by Lowcountry on 2008-09-18
> **tiresia said:**
> If you do not yet get MacOS9, try again this commands (with set-defaults too)

```
reset-nvram
set-defaults
reset-all
```

still nothing

---

### Post by tiresia on 2008-09-18
Boot-device and boot-file shouldn't be blank. Therefore you Mac does no know how to start. You can try:```
mac-boot
```
or```
boot hd:,\\:tbxi
```
I hope it works (if you don't find a solution you can even unplug the computer, remove the batteries from inside and wait for half an hour - after that you should be able to get to you MACOS9 again). I must go now. Let me know, if you can start with Ubuntu (you can try  another distribution, just to check it - like Fedora) or if you find another Mac you can try  your Installer-CD to be sure that it is OK

---

### Post by JonathanAppleseed on 2008-09-19
Hi there.

I'll throw in my two cents since I just got Xubuntu running on an old iBook G3.

First of all, I think you'll need to download version 7.10 or earlier because that was where support for the PowerPC processor ended. You'll also need to make sure that you're using the alternate install instead of the desktop or live cd.

I had the same problem as you for quite a while with the flashing question mark. In the end I got it to work, but I feel like it was a fluke. You'll need to use a CDR, and you'll need to burn at a low speed. 4-8x is fine. This has to do with CDRoms in these old systems not being able to read the burn. CDR disks are more reflective than CDRWs. On top of that, I've heard that disc's made in Japan (most Sony or Fujifilm) by Taiyo Yuden can make a difference in people's discs getting read. Again, better quality, more reflective.

Beyond that you might need to backtrack and check the md5 checksum on the downloaded file. Or simply burn multiple discs until one works. That's what I had to do.

Good luck.

---

### Post by Lowcountry on 2008-09-19
First, thanks for all the help so far.
A couple of updates:

I tried the alternate xubuntu 7.10.  Still, no go.
Then, I tried stable Debian net-install.  It boots it every time.  Unfortunately, it hangs at several place during the install.  Mostly while configuring the network.  Actually, this is before it begins installing, but it is progress.
So now, I'm downloading the full stable Debian, so it doesn't have to find the network during install and hopefully it will work after (it used to).
Any last suggestions of failsafe distros?  I only have 2 cds left.  Really, my only requirements are RhythmBox and the ablity to connect to my home network.  The purpose of this computer is to put in my garage and access my music.

Update:  The full version of Debian will not install either.  Only the net-install gets close.
Only one cd left.

---

### Post by Lowcountry on 2008-09-19
Update2:

I'm able to boot using the net-install cd, then at the boot prompt, I enter expert.  Then I remove the cd and insert the full cd.  It starts loading additional components, but something ALWAYS fails to read.  I hit enter to retry, but it fails.  I've checked the cd integrity and it's fine.
Maybe the computer just can't keep up.
It's a g3 333.  I believe it has 128 of ram.

---

### Post by tiresia on 2008-09-19
Why do not just start with the 'full' CD? 

If it fails with the CD, you can try to install from a USB stick. Here is a link
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html)

---

### Post by Lowcountry on 2008-09-19
> **tiresia said:**
> Why do not just start with the 'full' CD? 

If it fails with the CD, you can try to install from a USB stick. Here is a link
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html)

It won't boot from a full cd.  It makes no sense.
I'm currently trying ubuntu mini.  It gets pretty far in the process, the computer seems to restart at "detecting disks and other hardware".

---

### Post by tiresia on 2008-09-19
Do you know if the iMac has some extra hardware (PCI card, USB card)?

---

### Post by Lowcountry on 2008-09-19
> **tiresia said:**
> Do you know if the iMac has some extra hardware (PCI card, USB card)?

No, just what's built in.

---

### Post by cyberdork33 on 2008-09-19
honestly, it just sounds like bad burns/discs... I know that is not what you want to hear, but these CDROMs are REALLY picky about what they will read.

What you are describing sounds like every bad disc I have ever burned.

---

### Post by balebozb on 2008-09-29
Hi,
I have an iMac g3 400 DV: I had the same problem. I installed 7.04 from the live cd first, then I did a system update and upgraded to 7.10 using Update Manager. I then updated 7.10, then upgraded to 8.04  using Update Manager. This preserved my xorg settings from 7.04. Hope this helps.

---

### Post by DRM_free on 2008-10-01
Make sure you unplug all peripheral devices (USB, etc). Open Firmware on IMac G3's tends to fail to detect bootable CDs with you have non-Apple peripherals plugged in. For example, it kept spitting out my install CDs because I had a HP USB mouse plugged in. Unplugging the mouse allowed the Ubuntu 7.10 CD to boot fine.

After the installation is complete, you can plug the peripherals back in and keep them plugged.

---

