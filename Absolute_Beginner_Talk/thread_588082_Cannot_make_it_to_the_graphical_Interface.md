---
title: "Cannot make it to the graphical Interface"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by LoneEagle70 on 2007-10-23
Hi,

Brand new to Linux. I downloaded Ubuntu 7.10 CD Version and when I try to load from CD I do this:

1) I choose : "Start or Install Ubunto".
2) I see "Loading Kernel".
3) There is a loading bar with Ubuntu logo.
4) And I get a command line interface with "InitRAMfs" prompt.

I tried my laptop and a new HP desktop.

I want to get to the graphical version.

I am doing something wrong?

Note: I tried Knoppix and everything worked fine on my laptop.

---

### Post by bumanie on 2007-10-23
Did you download the live cd version or the alternate cd version? I suspect you downloaded the latter as it is a command line install. The live cd is graphical.

---

### Post by LoneEagle70 on 2007-10-23
How to know?

I went to
[INDENT][http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)[/INDENT]

The ISO size is:
ubuntu-7.10-desktop-i386.iso: 712,508 KB
ubuntu-7.10-desktop-amd64.iso: 713,566 KB (Tried and same result)

I think the command shell is called "Alternate"?

Thanks for your help! :)

---

### Post by OffAxis on 2007-10-23
it sounds like you've downloaded the alternate cd.
no problem.
it just doesn't have a desktop; that's all.
(you can try typing in **startx **and see what happens)
if you've got internet access just type in

```
sudo apt-get install ubuntu-desktop
```

and that will give you a graphical interface.

---

### Post by LoneEagle70 on 2007-10-23
> **OffAxis said:**
> it sounds like you've downloaded the alternate cd.
no problem.
it just doesn't have a desktop; that's all.
(you can try typing in **startx **and see what happens)
if you've got internet access just type in

```
sudo apt-get install ubuntu-desktop
```

and that will give you a graphical interface.
I do not think it is the alternate. Look at my previous post.

I tried "startx" and had an error.

For now, I only want to run from the CD and if working fine, do an installation on an Hard Drive.

Ok, I did a checksum of my IOS files:

61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso

I checked against the "http://mirrors.kernel.org/ubuntu-releases/7.10/MD5SUMS" and look fine.

Help! :)

---

### Post by OffAxis on 2007-10-23
whoops. you snuck a post in on me:oops:

I'm with you now. I thought you'd done an install and were booting to the command prompt, but you can't even get the live CD to boot to the Live Desktop.

you checked the .iso files for their checksum...Have you run the 'Check CD for defects' from the boot menu? (Could've had a problem while burning)

And how about the 'Safe Graphics Mode'?

---

### Post by LoneEagle70 on 2007-10-23
Your still with me, that great! :lolflag:

I tried 3 different CD Desktop 32, desktop 64, server 64).

Desktop 64:

* No matter what, I get always same result (from booting CD).
    - Setup or install
    - Safe mode
    - Verify CD

Here the screen result:

> BusyBox V1.1.3 (Debian 1:1.1.3-5ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)

For the server CD, I was asked to answer many questions like language, keyboard, blablabla. I just want to run from CD now. :(

The only thing I can see is an incompatibility with something (like Graphic Card or whatever). Is there a log I can see?

My desktop (nVidia) and laptop (ATI) are both recent.

---

### Post by OffAxis on 2007-10-23
okay, how's about turning off acpi?

From the boot menu hit **F6**
This will bring up the Boot Options text box, where you can add or subtract command line options from the default.

Note that at this point you can arrow key up and down the list.
Highlight the '**Boot Into Safe Graphics Mode**' and add this to the end of the options line
```
noacpi
```

and then boot.

if that works try disabling acpi on the normal boot.


by the way, it looks like your live cd log file is kept here:
**/casper.log**

based on this post
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/62679]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/62679")

---

### Post by LoneEagle70 on 2007-10-23
Thanks for your time.

I tried both 'noacpi' and 'acpi=off' and no luck.

I looked at the Casper.log and found errors on my usb card reader.
I unplugged the reader and now getting only a lot of 'error 0'.
The last message is 'unable to find a medium containing a live file system'.

---

### Post by OffAxis on 2007-10-23
bummer. I was hoping that was the answer.
was that the desktop or laptop?
(and under which of the live cd disks?)

the server iso that you downloaded is optimized for, well, servers, so it'll have you configure apache2 and mysql and such. It doesn't have a graphical desktop bundled into it, so I'm guessing you're using one of the other discs...

---

