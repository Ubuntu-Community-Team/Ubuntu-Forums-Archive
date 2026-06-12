---
title: "[SOLVED] Making a HDD based Image and Boot iso"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2008-04-17
Okay, so this is a three part question.

1.) Can I make an image of my HDD, complete with installed users, desktop configs, apps installed etc ?

2. Can I use this image to overwrite an existing HDD. e.g. Can I spend a day setting up my desktop, apps etc. then use this image as a 'Restore' point ? (I keep all data on a seperate partition.)

3. Can I put this image on a HDD partition; modify grub, and overwrite the Ubuntu partition to this 'Restore' point ?

(A bit like my Dell Ubuntu-Pre-Installed laptop does at the moment ?)

Cheers.

---

### Post by marufaberlin on 2008-04-17
Answer to all 3 questions is yes.

---

### Post by marufaberlin on 2008-04-17
It's called DD... you might wanna run it on a live cd. Also there's a tool called partimage. For your data, you might wanna use backup2l, doesn't put it in an image, but does incremental and timed backups.

---

### Post by philinux on 2008-04-17
> **WorldTripping said:**
> Okay, so this is a three part question.

1.) Can I make an image of my HDD, complete with installed users, desktop configs, apps installed etc ?

2. Can I use this image to overwrite an existing HDD. e.g. Can I spend a day setting up my desktop, apps etc. then use this image as a 'Restore' point ? (I keep all data on a seperate partition.)

3. Can I put this image on a HDD partition; modify grub, and overwrite the Ubuntu partition to this 'Restore' point ?

(A bit like my Dell Ubuntu-Pre-Installed laptop does at the moment ?)

Cheers.

Check out remastersys. [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by daengbo on 2008-04-17
Since this is open source, the answer to your questions is yes, but how easy the task will be depends.

you can use dd, as reported above, to choose your partition and run it through gzip to get rid of all the blank space. Make sure you do this from a live CD without the partition mounted.
If your partition is on /dev/sda1
to back up:
dd if=/dev/sda1|gzip > partition.img.gz

to restore
gunzip partition.img.gz|dd of=/dev/sda1

The grub auto-restore deal is more difficult, but you could at least create a small partition with linux and busybox on it, which when botted would run a script to do the restore, above. There may be other options I'm not thinking of right now.

All certainly do-able. I don't know if you were looking for a clickity-click method, though.

---

### Post by WorldTripping on 2008-04-17
Thats excellent news.

Just to clarify:

My /data partition (/dev/sda3) is fine. This is regularly backed up.

It's the root partition that I want to archive and restore.

So, I can use dd + gzip to archive the entire root partition to a different partition.

So by booting from a live CD I could use a command like:
dd if=/dev/sda1|gzip > /dev/sda2/image.gz

And to restore:
Boot from a live cd'
Format the root partition.
Then use the command;
gunzip /dev/sda2/image.gz|dd of=/dev/sda1

That would be exactly half of what I wanted.

So I suppose that I need to know about grub.

Are the devices mounted when grub comes up ?

Can grub run scripts ?

If grub can run scripts, would it be possible to have a script that went through the restore procedure i.e. format | gunzip + dd ?

As long as I ammended grub and wrote the script, this info would be part of the archive that I sent to the archive partition.

The cycle would be complete.

Hope that makes sense ?

---

### Post by WorldTripping on 2008-04-17
> **philinux said:**
> Check out remastersys. [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

Thanks for that.

I'm having a read now.

---

### Post by marufaberlin on 2008-04-19
No, grub cannot run scripts really exept some configuration files that need to be present on grub's root partition. This is usually where /boot is mounted. For your purposes, I would put grubs /boot/grub on a separate partition, if you haven't done that already. That way you can always edit grub's config. If you format and therefore remove grub's configuration, grub comes up with "ERROR 15" or "ERROR 22", don't remember which. Then you'll have to boot from a supergrub cd or something.

---

### Post by WorldTripping on 2008-04-21
Excellent, thanks for that.

I was only really looking at tinkering with grub to save myself a step.

I'm happy with dumping the whole of my perfectly set-up root onto a separate partition, booting with a CD and copying the lot over.

Cheers.

---

### Post by marufaberlin on 2008-04-21
Glad I could help you :-D

---

