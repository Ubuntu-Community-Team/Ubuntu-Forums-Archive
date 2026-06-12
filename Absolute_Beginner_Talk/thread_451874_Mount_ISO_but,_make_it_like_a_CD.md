---
title: "Mount ISO but, make it like a CD?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bitdefuser on 2007-05-22
I want to mount an ISO but, I want to trick linux into thinking it's an actual CD such as Daemon Tools.
Please help me out? Thanks.

---

### Post by %hMa@?b&lt;C on 2007-05-22
mkdir arbitrary-folder
sudo mount -o loop /path/to/iso arbitrary-folder
:)

---

### Post by bitdefuser on 2007-05-22
Did it but, where does it the CD appear?

---

### Post by %hMa@?b&lt;C on 2007-05-22
> **bitdefuser said:**
> Did it but, where does it the CD appear?

wherever your folder that I called "arbitrary folder" is probably in your /home/username directory
open up terminal and give me the output of "ls"

---

### Post by bitdefuser on 2007-05-22
I went there and found that folder but, it's not a CD.

---

### Post by %hMa@?b&lt;C on 2007-05-22
it is a folder with the contents of a cd inside.  that is how GNU/Linux treats CDs.

---

### Post by bitdefuser on 2007-05-22
So, I can't make it like a CD? :(
That means I have to burn them?

---

### Post by %hMa@?b&lt;C on 2007-05-22
> **bitdefuser said:**
> So, I can't make it like a CD? :(
That means I have to burn them?

it is the same as if it were a cd.  If you were to burn the iso to a cd it would act the same way as the mounted iso.  I dont really get what you are trying to do with this iso.

---

### Post by bitdefuser on 2007-05-22
Well, I have Cadega and I need it mounted so it can install from there but it throws errors at me saying it can not find a CD-Drive with contents in it.

---

### Post by %hMa@?b&lt;C on 2007-05-22
> **bitdefuser said:**
> Well, I have Cadega and I need it mounted so it can install from there but it throws errors at me saying it can not find a CD-Drive with contents in it.

tell the cedega program that your cd drive is located at /home/username/where/the/file/is/mounted and it should work

---

### Post by bitdefuser on 2007-05-22
How? I don't see any options for that.

---

### Post by Fred Doolie on 2008-02-07
I'm trying to do the same thing. Doing it this way causes the iso to show up as a hard drive with a hard drive icon on the desktop.  We want it to show up as a CD like a real CD would with the CD icon and the system thinking it is a real physical CD. You know, autoload and the system seeing another CDROM drive on the system and all that stuff.

Deamon Tools and that other thing that looks like a sheep icon can do it for Winblows. DON'T tell me that Winslows can do something that Ubuntu can't!




... It isn't true that Windows sucks. If it did it would be good for something.

.

---

### Post by PeterJS on 2008-02-07
In the eyes of linux there is no difference /dev/cdrom and some arbitrary iso. Both of them are byte streams that conform the iso9660 standard, nothing more nothing less (in user space, at the kernel driver level there are some differences, but those don't come in to play, ie not being able to "eject" an iso).

If you're trying to trick cedega in to thinking and image is a real disk then mount the image in an expected location. I use wine, not cedega, but being based off of wine I assume it handles devices about the same, if you looking in .cedega, or .wine there's a directory called dosdevices that are the devices that wine/cedega can recognize, they're just symlinks to other places in the real file system. If you look in there you should find one that looks like /media/cdrom0 or something along those lines, and so to trick cedega that's where you want to mount your image.

---

### Post by Thelasko on 2008-02-07
The simplest way to do it is with a program called[ G-scripts]("http://g-scripts.sourceforge.net/").  I don't recommend installing it from the sourceforge site.  I think I got it from [Automatix]("http://www.getautomatix.com/").  This allows you to execute scripts automatically to do a variety of things.  [Here is a How To for Ubuntu.]("https://help.ubuntu.com/community/NautilusScriptsHowto#head-0ddcd44dac3341317347cf5cfb099a6cdee97da0")  It even has a script for mounting an ISO.

---

