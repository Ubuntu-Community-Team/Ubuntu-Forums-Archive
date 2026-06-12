---
title: "Trouble when installing"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by schyffe on 2006-10-07
Hi, I recently downloaded the "ubuntu-6.06.1-desktop-i386.iso" image and tried to install it. From the boot menu, I first tried the install option, and it displayed that it loaded some configurations and did some setup etc..

After that, I get a blank screen. I tried changing the resolution to highest available, and then I saw a blinking cursor in the upper left side of the screen. It blinked for a while and I was waiting patiently, until it stopped blinking and everything seemed to stop, the CD-drive wasn't busy either.

After that I tried the safe colors option, which also gave me a blank screen at the same point everything else seems to fail.

The last thing I see is that the ACPI is loading when configuring, and about 3-5 lines more, then either I get a black screen or a blinking cursor.

I have really no idea what to try since I'm very new to all of this.

---

### Post by meborc on 2006-10-07
it seems your cd has problems... when booting cd try choosing the "verify cd" option... if it tells you that the verifying has failed, try to burn the image with lower speed... ;)

---

### Post by schyffe on 2006-10-07
No, I've verified the cd and no files are corrupt.

---

### Post by xpod on 2006-10-07
If your going to the bother of burning another cd youd be as well burning the "alternate cd" which is just as easy to use but its text based installer and is a good option when having load or install issues with the live cd`s.

Even folks with decent spes can find the live cd `s troublesome at times

EDIT:of course thats only any good if you want to install and not just try it out

---

### Post by schyffe on 2006-10-07
Thanks for the tip xpod, I guess that's currently my only option since I'm clueless about what to do.

---

### Post by CatKiller on 2006-10-07
There is a "noacpi" option for the installer. I'm not entirely sure on how you enable it, since I've not had to. Some implementations of [ACPI]("http://en.wikipedia.org/wiki/ACPI") can cause problems when installing operating systems.

---

### Post by schyffe on 2006-10-07
Now I've installed ubuntu using the alternative image. Guess what, the same thing happends when I try to boot ubuntu. This is getting really frustrating after a lot of re-installations. A weird thing happened though, when I'm stuck at the black screen with a cursor and press the shut down button, I'm brought to the login screen and after a few seconds the system is being shut down.

I had the hopes everything would work once I got ubuntu installed, but it feels like this brings me back to square one. Does anyone know how to get past this problem (or even what it could be)?

---

### Post by CatKiller on 2006-10-07
If it is an ACPI problem, you can turn it off in the BIOS. There's sure to be an option to turn it off in Linux, too - probably in GRUB. Have a look around.

---

### Post by Kacey on 2006-10-10
I am a big linux noob my self and am now switching from suse to ubuntu, but in suse I was having problems as well. You said in an earlier post that you are running two nvidia cards (SLI?) I my self am running two nvidia cards 6800 xt. What the problem I had was that X wanted to say that I was running dual monitors, what I had to do to fix this was edit the xorg.conf file and change some things in there. If you open that file and read it you will see it mention Monitor0 and monitor1 and also device1 and device0. Keep in mind this was with suse, I disabled the extra monitor and device and all was well in the world. As far as I know there is no SLI for linux. I will have to look around for some examples of how to do what I just said, but at lest now you can see a bit more of what is going on.

---

