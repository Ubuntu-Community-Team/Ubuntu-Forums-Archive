---
title: "Xubuntu Installation HELP WANTED!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by n3rdkw on 2007-10-07
Okay I'm completely new to linux but I'm... not so new to command lines and computers in general
Well I'm trying to install xubuntu 7.04

So I dl the xubuntu-7.04-desktop-i386.iso

Burn the image onto a cd using Nero burner

And then set the BIOS so that it boots from CD first, floppy second and HD last

All right now I put in the CD, reboot the computer

IT seems to be loading from the CD fine for a bit

After about 2 pages of txt loading, it finally stops with some copy right crap 

and says something like "running dos safe mode" or something like that
and leaves me with something like this:
[dos] A:/>

What is wrong?

---

### Post by Kilz on 2007-10-08
> **n3rdkw said:**
> Okay I'm completely new to linux but I'm... not so new to command lines and computers in general
Well I'm trying to install xubuntu 7.04

So I dl the xubuntu-7.04-desktop-i386.iso

Burn the image onto a cd using Nero burner

And then set the BIOS so that it boots from CD first, floppy second and HD last

All right now I put in the CD, reboot the computer

IT seems to be loading from the CD fine for a bit

After about 2 pages of txt loading, it finally stops with some copy right crap 

and says something like "running dos safe mode" or something like that
and leaves me with something like this:
[dos] A:/>

What is wrong?

This is linux, dos is a microsoft product, are you sure it said dos?

---

### Post by LaRoza on 2007-10-08
> **n3rdkw said:**
> 

and says something like "running dos safe mode" or something like that
and leaves me with something like this:
[dos] A:/>

What is wrong?

That can't be right, DOS has nothing to do with Windows, and DOS uses \ not /.

Did you check the CD for defects?

---

### Post by freebird54 on 2007-10-08
First thing that comes to mind is that the CD was not burned as an ISO (that is to say IMAGE) but was burned as a file - and the machine booted off an old floppy perhaps??

Make sure the CD is burned as an image (not a file) and that the BIOS is set to try the CD drive first...

If this is not clear - ask for more detail!

---

### Post by kerry_s on 2007-10-08
burn it as a image at 4x for best results.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by n3rdkw on 2007-10-09
I'm sure it's burned as an IMAGE.
And I set the bios so it loads ONLY from CD.
It seems to detect that there's something on the CD and attempts to boot from it, but it seems to kick out.
I've burned the disk twice, and they're both fine but same result
=/

And yes it does say DOS, as to the / \, I forgot which one it was.

---

### Post by adrian15 on 2007-10-09
> **n3rdkw said:**
> I'm sure it's burned as an IMAGE.
And I set the bios so it loads ONLY from CD.
It seems to detect that there's something on the CD and attempts to boot from it, but it seems to kick out.
I've burned the disk twice, and they're both fine but same result
=/

And yes it does say DOS, as to the / \, I forgot which one it was.

You should not use the Nero feature: Make this CD bootable because it adds an emulated DOS floppy and that's what you do not want to happen. Untick the option and you are done.

adrian15

---

