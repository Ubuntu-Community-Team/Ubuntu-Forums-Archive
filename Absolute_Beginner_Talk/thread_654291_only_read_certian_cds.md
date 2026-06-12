---
title: "only read certian cds???"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by tommytomthms5 on 2007-12-30
so i installed ubuntu for my mom who was pissed with vista....

but she wants to run a few windows only files required by her school so i installed wine (easy) popped in the cd and nothing happened so i went to "computer" and clicked the drive it says theres no disk in the drive when i know there is

so i stuck in a different cd... actually a data dvd and it popped right up needless to say i was confused

so now ive tryed about 10 cds and maybe 3 of those worked....:confused:

can anyone point me anywhere with this????

---

### Post by tommytomthms5 on 2007-12-30
bump

---

### Post by Paulmd on 2007-12-31
> **tommytomthms5 said:**
> yo dont ignore me


Patience. You aren't being ignored until at least a day has passed.

Anyway: back to the question.

Reading only certain cds is often a fault of the drive itself.

For example:

1) reads dvs but not cds: this is usually a mechanical failure. dvd drives have 2 lasers, one for cds, the other for dvds. this means one of them has failed.

2) Reads factory disks but not burns: this is either mechanical, or firmware related. writable cds are less reflective than factory cds (70% vs 90%), if the lens of the optical drive is dirty, or the laser is failing, cdrs are the first victims. (there are lens cleaner cds available, and on laptops the lens is readily accessible, you can clean it with alcohol and a q-tip)

An issue with firmware is possible, as well. The symptoms of that are where it reads certian brands of cdrs and not others. Many cds, and dvds are firmware-upgradeable. Especially burners. 

3) Disks that are scratched... some drives are more tolerant of this than others. Sometimes firmware updates help. Not usually. You can repair minor scratches on cds.

A reads in windows- but not in linux issue is.... unusual. And no you can't test this by trying it in a windows machine, that won't test the drive itself. All that may do is eliminate a few bad disks. Only way to test that would be on a dual boot system.

---

### Post by SOULRiDER on 2007-12-31
Is it possible that they have some sort of copy protection on them?

---

### Post by Hallvor on 2007-12-31
> **tommytomthms5 said:**
> so i installed ubuntu for my mom who was pissed with vista....

but she wants to run a few windows only files required by her school so i installed wine (easy) popped in the cd and nothing happened so i went to "computer" and clicked the drive it says theres no disk in the drive when i know there is

so i stuck in a different cd... actually a data dvd and it popped right up needless to say i was confused

so now ive tryed about 10 cds and maybe 3 of those worked....:confused:

can anyone point me anywhere with this????

What kind of "windows only" files are they?

---

### Post by Paulmd on 2007-12-31
> **SOULRiDER said:**
> Is it possible that they have some sort of copy protection on them?

Maybe if they were game disks. But even copy protected software doesn't go to the extreme of making the disk unreadable, and therefor not installable.

---

### Post by SOULRiDER on 2007-12-31
> **Paulmd said:**
> Maybe if they were game disks. But even copy protected software doesn't go to the extreme of making the disk unreadable, and therefor not installable.

You never know what those windows users can come up with :-k

In any case, if you can read the disk in another computer, try copying the files to some other medium, like a USB stick and then just copy them over.

---

### Post by TidusBlade on 2007-12-31
I know for sure that UDF discs cannot be read by linux, tried for a long time, but to no avail, so if if the CD/DVD filesystem is UDF, then linux wont read it, theres also probably a few more filesystems linux cant read.
Your best bet is to drag them onto a USB/External HD or another disc and drag them into your linux computer ;)

---

### Post by Paulmd on 2007-12-31
> **TidusBlade said:**
> I know for sure that UDF discs cannot be read by linux, tried for a long time, but to no avail, so if if the CD/DVD filesystem is UDF, then linux wont read it, theres also probably a few more filesystems linux cant read.
Your best bet is to drag them onto a USB/External HD or another disc and drag them into your linux computer ;)


I had forgotten about evil packet-writing. Thanks for the reminder. That doesn't work all that great even on Windows. You have to install third party software. Nobody else can read your compilations if you do packet writing, :(

Wikipedia says linux can read some versions of UDF.

[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

also 

[http://sourceforge.net/project/showfiles.php?group_id=295](http://sourceforge.net/project/showfiles.php?group_id=295)

---

### Post by tommytomthms5 on 2007-12-31
> **SOULRiDER said:**
> 

In any case, if you can read the disk in another computer, try copying the files to some other medium, like a USB stick and then just copy them over.

i like that idea thats what may have to happen


also im sure its reading the disks fine i think its just not wanting to mount them so i think it is something to do with the file system on the disks....

---

### Post by SOULRiDER on 2008-01-01
Try mounting them manually.

---

