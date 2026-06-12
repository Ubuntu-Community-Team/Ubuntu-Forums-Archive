---
title: "Mac Mini won't boot from CD"
date: 2011-04-10
forum: Apple Hardware Users
---

### Post by Ecstatic23 on 2011-04-10
Hi everyone,
I've had a hell of a time trying to install Ubuntu on my Mac Mini.

I deleted my Bootcamp Windows 7 and created a new partition for Ubuntu, but I'm unable to boot the Mac Mini from a CD, DVD or USB (with Ubuntu).

I have burned Ubuntu on to the DVD's with an ISO burning tool, and uNetBootin for the USB. The USB did show up in the Mac boot menu and gave me the option to install Ubuntu from a black screen, but after that it just black screened and continued on to boot OS X.

Thank you for reading. Please help :3

---

### Post by Ecstatic23 on 2011-04-12
BUMP - Need urgent help.

---

### Post by hansdown on 2011-04-12
Hi Ecstatic23.

Start with the disc in, and restart the system.

Hold the "C" key, till it boots from disc.

---

### Post by Ecstatic23 on 2011-04-12
> **hansdown said:**
> Hi Ecstatic23.

Start with the disc in, and restart the system.

Hold the "C" key, till it boots from disc.

The screen goes black for a while, then shows the Apple logo and starts booting OS X :l

---

### Post by imac_89 on 2011-04-12
What Ubuntu iso do you use?
What mac mini do you have?

I have successfully booted off the CD/DVD in both i386 and amd64 flavours. 

What is your process when you boot off of the CD?

---

### Post by Ecstatic23 on 2011-04-13
> **imac_89 said:**
> What Ubuntu iso do you use?
What mac mini do you have?

I have successfully booted off the CD/DVD in both i386 and amd64 flavours. 

What is your process when you boot off of the CD?

Ubuntu ISO - 11.04 BETA, amd64
Mac Mini - Late 2010
Hold 'c' at start up

---

### Post by imac_89 on 2011-04-13
Hmmm, so booting off the disc is a no go, what did you use to burn the iso?

I just drag the file to Disk Utility and hit burn.

---

### Post by Ecstatic23 on 2011-04-14
> **imac_89 said:**
> Hmmm, so booting off the disc is a no go, what did you use to burn the iso?

I just drag the file to Disk Utility and hit burn.

Disk utility and another ISO tool for windows.

Could there be something wrong with my disc drive?

---

### Post by imac_89 on 2011-04-14
Do you have another drive to test it with?

Also, have you tried booting off one of the i386 (I know it isn't 64 bit, but bear with me)?

What about holding down the 'option' key while starting, although this is generally the same as using 'C' I guess.

---

### Post by cfr42 on 2011-04-15
Does the Mac Mini use an AMD processor? I thought they all used Intel?

(I guess this is what the previous reply is getting at, too?)

---

### Post by imac_89 on 2011-04-16
It still baffle me that you can't get your mini to boot. i am officially stumped :sad:

Anyone else have an idea?

---

### Post by Ecstatic23 on 2011-04-17
> **imac_89 said:**
> Do you have another drive to test it with?

Also, have you tried booting off one of the i386 (I know it isn't 64 bit, but bear with me)?

What about holding down the 'option' key while starting, although this is generally the same as using 'C' I guess.

I haven't tried the i386. I'll download it now. Option/Alt gets me a little bit further, Shows me an option for 'EFI Boot' which then shows me this:

> GNU GRUB version 1.99"rc1-6ubuntu1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

Grub> _

:L

> **cfr42 said:**
> Does the Mac Mini use an AMD processor? I thought they all used Intel?

(I guess this is what the previous reply is getting at, too?)

Intel Core 2 Duo.

---

### Post by Ecstatic23 on 2011-04-17
Just attempted installing the i386 copy. Unfortunately it does the same thing.

---

### Post by Ecstatic23 on 2011-04-18
Still need help :L

---

### Post by imac_89 on 2011-04-22
Hmm, go back to using the Option key during boot, select the other Boot CD icon, not the EFI boot. What result do you get?

---

### Post by Slimmons on 2012-06-21
Hey, I know this thread is oldish, but I've got the exact same problem.  I got a mac mini, and I put Ubuntu 10.04 on it, and after I upgraded it to 10.10, I restarted.  From that point on, nothing worked, so since my original plan was just to upgrade all the way to 12.04, I burnt a dvd of 12.04.  I have tried all the ways listed above to get to my boot menu, and I've tried several command line options since I was able to install puppylinux.  Yes, Puppy linux dvd had no problem starting up, but I've tried 12.04's dvd over and over, and no luck with anything.  The dvd is not corrupt, I have checked it on other computers and it's working fine.  Anybody have new ideas?

---

