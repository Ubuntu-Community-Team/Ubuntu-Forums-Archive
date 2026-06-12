---
title: "Creating ISO image of Ubuntu 7.04 doen't produce the same md5sum"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-26
Hi,
I have downloaded Ubuntu 7.04 from ubuntu.com web page. I have checked the md5sum and got official check sum number (e296e3468358789904097fc8df29609a) for ubuntu-7.04-desktop-i386.iso. I burn CD with this ISO image and then I have deleted the iso file. Now I have created ISO image from CD (Nero on Windows XP). Nero successfully created ISO image (no errors returned). I have checked md5sum of ISO file created from Neru. The md5sum number is not the same as downloaded number. Why?
Thanks,
Abcuser

---

### Post by kagashe on 2007-04-26
> **abcuser said:**
> Hi,
I have downloaded Ubuntu 7.04 from ubuntu.com web page. I have checked the md5sum and got official check sum number (e296e3468358789904097fc8df29609a) for ubuntu-7.04-desktop-i386.iso. I burn CD with this ISO image and then I have deleted the iso file. Now I have created ISO image from CD (Nero on Windows XP). Nero successfully created ISO image (no errors returned). I have checked md5sum of ISO file created from Neru. The md5sum number is not the same as downloaded number. Why?
Thanks,
Abcuser

Nero must have added some line like "it produced the iso".:lolflag:

---

### Post by abcuser on 2007-04-26
Hi,
is there any open source or freeware program on Windows/Linux to just burn a CD without any additional info. I would like to have a tool that works on Windows and on Linux to have no problems using that on both systems.
Thanks,
Abcuser

---

### Post by Cypher on 2007-04-26
Since you've already burned the CD, why do you still want the .ISO??

---

### Post by Sef on 2007-04-26
> is there any open source or freeware program on Windows/Linux to just burn a CD without any additional info


Yes, there is[ ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by az on 2007-04-26
You can make an iso out of a cd using dd (datadump)

dd if=/dev/cdrom of=file.iso

---

### Post by abcuser on 2007-04-26
> **Cypher said:**
> Since you've already burned the CD, why do you still want the .ISO??
My friend would like to have a copy of my Ubuntu CD. So I just created ISO image and burn a new CD.

---

### Post by Cypher on 2007-04-26
> **abcuser said:**
> My friend would like to have a copy of my Ubuntu CD. So I just created ISO image and burn a new CD.
Ahh OK, makes sense..I was just curious..that's all..:)

---

### Post by abcuser on 2007-04-26
> **Sef said:**
> Yes, there is[ ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").
Thanks. Is this program also available on Linux? I am just collecting Windows - Linux programs. So the same program on both operating systems (some thing like Firefox, Thunderbird, etc).

---

