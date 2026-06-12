---
title: "[SOLVED] Verifying CD / DVD burn"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by e_james on 2007-10-03
Using Windows I have at least two applications which allow for verifying data after burning a CD or DVD. Is there any linux software which has the same facility. Using this facility I have learned that some makes of discs will make coasters as often as 1 in 3 and others as infrequently as 1 in 100.

---

### Post by master_kernel on 2007-10-03
You can probably verify the md5sum (hash) on both the burned CD and ISO file.

---

### Post by e_james on 2007-10-03
I freely admit there are many things I don't know but, from what I do know, I don't think it is logical to compare an md5sum from a CD to the md5sum of an ISO file, unless you mean the contents of the ISO file. Is it possible to obtain an md5sum for a selection of files instead of just one? If so, it would probably work for a data CD or DVD but not for a bootable CD which I believe is actually split into 2 parts. One part looks like a data CD and the other looks like a floppy disc (to the bios at least). I've been trying to understand bootable CDs and I haven't quite worked out the floppy disc part yet.

---

### Post by bodhi.zazen on 2007-10-03
You have a few options.

k3b is my favorite burning application because it checks the integrity of the burn ...

Brasero will also do this as well ...

[http://www.movingtofreedom.org/2007/04/08/brasero-does-the-cd-burning-job-in-gnome-ubuntu/](http://www.movingtofreedom.org/2007/04/08/brasero-does-the-cd-burning-job-in-gnome-ubuntu/)

---

### Post by e_james on 2007-10-04
bodhi.zazen

Thanks for your suggestions. I will check those out as soon as I get the opportunity. I think that's one step closer to leaving Windows behind. I need to have the data verified because I usually delete the source data as soon as I am satisfied with the DVD. I need the space for the next one.

---

### Post by e_james on 2007-10-04
I have done some tests with both k3b and Brasero.

Both have the same flaw when used with a laptop; they eject the disc and are unable to reload it. k3b has a setting "Do not eject disc after write" but it doesn't apply this between write and integrity check, only after the check. I think the linux software is ejecting and reloading the CD as a quick and dirty strategy to get the CD mounted for the integrity check. What's wrong with the command "mount /media/cdrom0"?

k3b also seems to have a bug. it will only carry out the integrity check successfully if writing directly from an image file. If the project is a data CD, the integrity check fails to start even if an image file is created as part of the write.

It appears that Brasero is generally suitable for my purposes.

Thanks again

---

### Post by philinux on 2007-10-04
I'm using k3b. Burnt an iso last night the disk comes out but goes back in straight away for check

---

### Post by e_james on 2007-10-04
Most laptops have no motors to take the disc back in.

---

### Post by philinux on 2007-10-04
Ah. See your dilemma. I've found that with k3b I dont bother to  verify much now. It's pretty good and I've not had  one coaster.

---

### Post by bodhi.zazen on 2007-10-04
> **e_james said:**
> I have done some tests with both k3b and Brasero.

Both have the same flaw when used with a laptop; they eject the disc and are unable to reload it. k3b has a setting "Do not eject disc after write" but it doesn't apply this between write and integrity check, only after the check. I think the linux software is ejecting and reloading the CD as a quick and dirty strategy to get the CD mounted for the integrity check. What's wrong with the command "mount /media/cdrom0"?

k3b also seems to have a bug. it will only carry out the integrity check successfully if writing directly from an image file. If the project is a data CD, the integrity check fails to start even if an image file is created as part of the write.

It appears that Brasero is generally suitable for my purposes.

Thanks again

\o/

> **e_james said:**
> Most laptops have no motors to take the disc back in.

>_<

---

### Post by PCZahra on 2007-10-31
it's not neccesarily the software. sometimes the burner itself spits the disc out when it gets the signal that it's finished, and if you're lucky the software will tell it to pull it back in. I wrote my own burner program once and found the device did just that.

---

