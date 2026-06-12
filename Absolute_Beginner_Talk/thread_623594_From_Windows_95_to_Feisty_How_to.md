---
title: "From Windows 95 to Feisty: How to??"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-11-26
A friend was given an O - L - D computer: 1G HD, 24M RAM and 100MHz CPU. I tried loading Linux Tinyme, Puppy and Feisty - all to no avail. It's as though the ISO-burned CDs are ignored by Windows. Sidenote: The disks work fine on my LinuxFeisty machine.

I know zilch about W95, so I need some detailed, lead-the-dumbass-by-the-nose help. :confused:

I'm now off to try to find an ISO D/L mirror so I can burn a copy of DamSmallLinux 4.0. <--That one or Puppy appear to be good candidates for the dinky HD and sub-marginal memory.

---

### Post by aktiwers on 2007-11-26
I would go for DamnSmallLinux
[http://damnsmalllinux.org/download.html](http://damnsmalllinux.org/download.html)

---

### Post by jachymc on 2007-11-26
Do not try it. You have to try something more lighter, like slackware. It is not that userfriendly, as Ubuntu is, however, it is here for couple of years and will still be. You'll like it, I'm sure ;)

---

### Post by skillet on 2007-11-26
the cdrom is so old that you wont be able to boot it from cdrom. ( I have a few of em ) you are going to have to boot from a floppy... Do you remember those things? heh... Anyways DSL or Slackware would be good. I would run X on it tho. It would kind of be couter-productive. Slackware would what I would install on it. If you really want to learn Slackware is where its at.

---

### Post by jimmj43 on 2007-11-26
HOOT! :)

I just gave the DSL a test drive on this machine running just from the CD. All things considered, it's pretty doggone impressive.

I know the CD ROM on the OLD machine works 'cause I inserted and viewed some of the contents of a CD I'd burned prior to blowing W2kpro away in favor of Feisty on this machine.

I also tried swapping out HDs with a few I have laying around. But they've all been wiped, and fared no better.

I'll try the DSL site. <--Thanks for that. :KS

---

### Post by stinger30au on 2007-11-26
wow!! pentium 100 or 486 at 100Mhz??

either way, an old clunker.

would be interesting to see linux running on it just to see the blazing speed

---

### Post by jimmj43 on 2007-11-27
It looks like I've found the hitch. The older machine needs a boot floppy in order to 'see'  and read the install disk. I've found & D/L'd the boot  ISO. Now comes the punchline from left field.
I have no idea how to make a floppy using Feisty. Burn a disk? Piece o' cake. Make a floppy? Beats hell outta me!

---

### Post by ceduriki on 2007-11-27
Hahaha. No way, that won't ever work. My suggestion, get into this decade wiht a new computer. dells are pretty cheap. Or you can go to newegg buy some parts and build one.

---

### Post by CptPicard on 2007-11-27
I'm pretty sure you won't be able to create a boot floppy for Ubuntu. The RAM in the machine isn't sufficient anyway, so there's no point really. It's would make a perfectly good command-line box, but getting X running with anything but the most Spartan window manager is going to be tough :)

Linux on machines like that *is* very possible, after all, in the 90s I started with Linux on that sort of hardware, when it was actually current stuff...

---

### Post by jimmj43 on 2007-11-27
Maybe I need to clarify. I'm trying to install Linux on a very old box that has sharply limited capabilities: 1G HD, 24M RAM, and a 100MHz Pentium currently loaded with W95.

On this, an entirely separate machine, currently running Feisty, I want to create a boot floppy for the older machine. But I don't know how to create a floppy using Feisty.

---

### Post by Vince4Amy on 2007-11-27
I think what they're trying to say is, there's no point of even creating a boot floppy as Feisty won't run properly with those specs. I do however recommend Damn Small Linux like suggested earlier.

---

### Post by maybeway36 on 2007-11-27
24M RAM? Probably the only thing that will run on that is FreeDOS.

---

### Post by Mazza558 on 2007-11-27
How on earth did Win95 ever run on that?

---

### Post by Steve1961 on 2007-11-27
You could always use a Slackware boot floppy to get the system up and running:

[http://www.slackware.com/install/bootdisk.php](http://www.slackware.com/install/bootdisk.php)

---

### Post by jimmj43 on 2007-11-27
One. More. Time.

I want to install DSL (DamnSmallLinux) on the old machine - it's <50M in size.

I got the Boot floppy info from a lead in the DSL forums, and D'L'd it to THIS machine which runs Feisty.

I just need to learn how to create a floppy using Feisty.

I already tried burning a disk of the boot data. Fail. The OLD machine didn't recognize that either. Apparently, it's gotta be in the format of a floppy. Also unanswered is whether the ISO image of the boot data I D/L'd is suitable for creating a floppy.

---

### Post by lespaul_rentals on 2007-11-27
You might try mounting the .iso intended for the floppy, like so:

```
sudo mkdir /mnt/<name of desired mountpoint>
```

Then, run this command to mount it:

```
mount yourimage.iso /mnt/<name of desired mountpoint>/ -o ro,loop
```

Then, just copy the files from the mounted .iso to the floppy.

---

### Post by jimmj43 on 2007-11-27
Lemme see how weak my translating skills are. 

> You might try mounting the .iso intended for the floppy, like so:

Code:

sudo mkdir /mnt/<name of desired mountpoint>

Then, run this command to mount it:

Code:

mount yourimage.iso /mnt/<name of desired mountpoint>/ -o ro,loop

Then, just copy the files from the mounted .iso to the floppy.

"Code" <--pretty self-explainatory in itself, but how do I get to the place where I enter it? Did I mention I'm a raw Linux noob?

"sudo mkdir /mnt/<[COLOR="Red"]name of desired mountpoint[/COLOR]>"

That would probably be: A drive <--If so, how to I get to that place?

---

### Post by lespaul_rentals on 2007-11-27
Oh, sorry about that.  You would input these commands in the command-line shell/terminal.

It's actually sort of a hassle to find out device names, even for me.  Does your floppy auto-mount when you insert it?

---

### Post by caffienefree on 2007-11-27
Does this help?

[http://www.linux.com/base/ldp/howto/IBM7248-HOWTO/floppies.html](http://www.linux.com/base/ldp/howto/IBM7248-HOWTO/floppies.html)

---

### Post by jimmj43 on 2007-11-27
Lespaul, no. Running Feisty if I insert a floppy nothing (that I can see) happens.

Caffinefree, that site might help more if it came with a translator - geekspeakshorthand-to-English. What does "cd" mean?

Sidenote: Now I gotta backtrack to find out what flavor of Linux DSL is - Debian, Gentoo, Mandrake, whatever.. GAH!

But that's MY problem! You guys seem to be pointing me in the right direction. Please don't stop!

Thanks! :)

---

### Post by caffienefree on 2007-12-04
Those are commands: cd means "change directory".

What they were basically saying is to save the debian disk image, open up a terminal, go to where you saved it (the desktop, for example, would be cd Desktop), put a floppy disk in the drive, and execute the command they gave you...

> dd if=debian-7248-boot.img of=/dev/fd0 bs=36b
 

---

