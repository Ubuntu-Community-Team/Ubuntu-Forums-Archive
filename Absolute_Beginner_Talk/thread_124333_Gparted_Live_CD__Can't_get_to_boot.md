---
title: "Gparted Live CD ??? Can't get to boot ?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by petef on 2006-02-01
Downloaded Gparted live CD iso and wrote it to CD on a Windows XP laptop, but I can't get it to boot on my Ubuntu machine ? Any ideas ? 

Ive tried writing the iso twice on different CD's and at very slow speeds (4x)

Thanks in advance 

Pete

---

### Post by cotcot on 2006-02-01
Is your BIOS looking for the CD first ? 

Maybe try another live CD with GParted or QTParted (I use Kanotix or Knoppix because I get errors with GParted)

---

### Post by petef on 2006-02-01
Thanks for the reply.

I tried burning a second CD of gparted but still won't boot. Just tried it on a second machine at home still no good ?

Any idea how to do this from the terminal ?

cheers

Pete

---

### Post by steve.horsley on 2006-02-01
Make sure you are burning the .ISO file as an **image file**, not as a data file. In Nero there is a menu option for burning an image file. Not sure about other packages, but I think the word image is the important thing. An ISO image file actually contains the entire CD filesystem within it (including a boot sector) - you don't want to write it as data inside another CD filesystem.

---

### Post by rstritmatter on 2008-06-11
> **steve.horsley said:**
> Make sure you are burning the .ISO file as an **image file**, not as a data file. In Nero there is a menu option for burning an image file. Not sure about other packages, but I think the word image is the important thing. An ISO image file actually contains the entire CD filesystem within it (including a boot sector) - you don't want to write it as data inside another CD filesystem.

I'm having the same problem. I'm trying to use gparted to resize some windows partitions before reinstalling ubuntu. Bios is set to read cd/dvd drive and file on cd is .iso.  But the computer still will not boot to the cd and instead goes into windows.  I've had this happen numerous times. Nothing seems to work.:confused:

Any clue?

Thanks in advance for your help.

---

### Post by meierfra. on 2008-06-11
> file on cd is .iso

This means  that you burned it wrongly.

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by drs305 on 2008-06-11
I just downloaded and burned the Gparted cd this afternoon. When I open it up in nautilus I see 4 files and 3 folders: isolinux, live and .disk. It boots normally.

---

