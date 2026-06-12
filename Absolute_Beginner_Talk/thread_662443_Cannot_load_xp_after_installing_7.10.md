---
title: "Cannot load xp after installing 7.10"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by masonj7 on 2008-01-08
installed 7.10 after clean install of xp pro.  manually partitioned the drive.  now grub will load ubuntu but when loading windows i get an error message.  i still have access to my files on xp.  

have tried the following:
added commands to grub menu.lst file
changed the flag for the windows partition to boot from within ubuntu
tried to use xp install cd to boot into recovery mode (would not load)
tried to use live cd version of grub - would not load
tried the ultimate boot cd - did not work

what information do you need to help me with this problem?

---

### Post by yaknowwat on 2008-01-08
do you know if the error message is from Grub or from Windows.

if it is from GRUB then more than likely GRUB is being pointed to the wrong partition / drive.

please post the menu.lst

---

### Post by masonj7 on 2008-01-08
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6cc090a3-b754-42ce-8941-af13a5006a59 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6cc090a3-b754-42ce-8941-af13a5006a59 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

---

### Post by yaknowwat on 2008-01-09
everything seems to be correct which is not a good sign.

Try this.
```

title		Windows XP Professional
root		(hd0,0)
map		(hd0,0) (hd0,0)
map		(hd0,0) (hd0,0)
savedefault
makeactive
chainloader	+1

```

after testing it out please say what the error was if this does not work.

---

### Post by masonj7 on 2008-01-09
would it have anything to do with windows and ubuntu partitions listed on the extended drive instead of the primary?  i read somewhere that that might be the problem, but i do not know how to change that.

---

### Post by masonj7 on 2008-01-09
changing that led to a familiar code

error 12:  invalid device requested


if i cannot dual boot between windows and ubuntu what do i need to do to access the xp partition and get it started by itself and then reinstall ubuntu onto a secondary hard drive instead of a partition?

---

### Post by yaknowwat on 2008-01-09
That would explain a lot as i hear windows does not boot under an extended partition.

edit : your current error 12 means that it might just be a wrong pointer for GRUB.

though it is slightly possible what i heard was wrong and you might be able to use.

title		Windows XP Professional
root		(hd0,2)
map		(hd0,0) (hd0,2)
map		(hd0,2) (hd0,0)
savedefault
makeactive
chainloader	+1

to boot windows .

truth is is the way Grub works is it goes for non swap paritions in their labeled order.

My guess is that the logical partition got labeled as 0,0 ubuntu 0,1 windows xp 0,2
unless you did some more partitioning.

---

### Post by masonj7 on 2008-01-09
now getting the following:

error 13: invalid or unsupported executable format

if i wanted to blow out the ubuntu partition, would the system revert back to normal? or would i then have no os at all?

---

### Post by yaknowwat on 2008-01-09
> **masonj7 said:**
> now getting the following:

error 13: invalid or unsupported executable format

if i wanted to blow out the ubuntu partition, would the system revert back to normal? or would i then have no os at all?

From the sounds of it you changed Windows Partition completely.

error 13 is pretty interesting.

probably should of asked this earlier but can you open up the partition editor and take a picture please.

(Printscreen button)
upload to something like [http://imageshack.us/](http://imageshack.us/)

---

### Post by masonj7 on 2008-01-09
[http://img135.imageshack.us/my.php?image=screenshotus5.png](http://img135.imageshack.us/my.php?image=screenshotus5.png)

---

### Post by masonj7 on 2008-01-09
[[img=http://img135.imageshack.us/img135/1604/screenshotus5.th.png]](http://img135.imageshack.us/my.php?image=screenshotus5.png)

this should be it

---

### Post by defaultuser01 on 2008-01-09
The same thing happend to me. I got a different error message though. I was told that when I installed Ubuntu that it hid the windows partition. I loaded ubuntu... System>Administration>Partition Editor and changed the flag for the partion windows xp was on.

---

### Post by masonj7 on 2008-01-09
i changed the flag to boot.  it wasn't hidden before though.  is your windows partition after the extended break or is it primary before the extended part?

---

### Post by yaknowwat on 2008-01-09
ok... having XP as the extended partition is the problem and to fix it i will admit this part is going to take hours of partition time.

1. unmount the NTFS volume.
2. resize the NTFS down to its smallest size possible 44GB or so.
3. reduce the extended partition down until all the unallocated space is *infront of it
4. format the space in front of it to NTFS, there should be about 150GB.
--steps 1-4 will take all night most likely.
--when you wake up.
move all files from the NTFS in the extended to the newly created NTFS.

then use.

title Windows XP Professional
root (hd0,2)
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
savedefault
makeactive
chainloader +1

in GRUB to boot attempt a boot into XP this most likely will work.
if it does then you can proceed to delete the extended partition.

It is suggested to backup and important data just in case and also use a LiveCD.

---

### Post by masonj7 on 2008-01-09
thanks, i will try that and get back to you.  it may be a few days because of work and such, but hopefully it will work.

---

### Post by shareMenaPeace on 2008-01-09
Hi, you might also want to try out this grub super disc 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by yaknowwat on 2008-01-09
> **shareMenaPeace said:**
> Hi, you might also want to try out this grub super disc 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Don't think he'll really need that after see'ing his partition arrangement.

error 13 was from his Windows XP being in an extended partition the way it seems.

---

### Post by shareMenaPeace on 2008-01-09
Ok, i just thought he could try this before using the mentioned very long way :D
But i do not know much about this yet ...

Cheers
:popcorn:

---

### Post by teslarage on 2008-01-09
yaknowwat,

I'm having the same problem. My partition editor looks exactly the same as masonj7's.

Your suggestion to resize NTFS partition is a no-go. NTFS partition cannot be resized.

---

### Post by masonj7 on 2008-01-10
ntfs can be resized with partition magic boot disc or by unmounting the drive first in the grub.  i am still working on getting the time to make sure the changes go well.

there needs to be something about this as a sticky for xp dual boot users.  or something changed about how the partitioner works with windows.

---

