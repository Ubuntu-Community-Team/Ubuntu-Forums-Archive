---
title: "installation of ext3 filesystem problem"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by psixpsi on 2008-03-12
hi all!!

i'm trying to install gutsy on a machine where previously worked vista.
when i run LiveCD (both graphical and alternate) it goes up to
writing partitions and then quickly stops, saying it cannot write 
ext3 filesystem.
the drive is 160G, i choose the guided partitioning.

every run of LiveCD takes just ages---it does something extensively 
with the hard drive and spits messages like:

I/O Error on device sda3, logical block 8

 i'm completely perplexed...

thanks for any help!
-psixpsi

---

### Post by mikeyphi on 2008-03-12
> **psixpsi said:**
> hi all!!

i'm trying to install gutsy on a machine where previously worked vista.
when i run LiveCD (both graphical and alternate) it goes up to
writing partitions and then quickly stops, saying it cannot write 
ext3 filesystem.
the drive is 160G, i choose the guided partitioning.

every run of LiveCD takes just ages---it does something extensively 
with the hard drive and spits messages like:

I/O Error on device sda3, logical block 8

 i'm completely perplexed...

thanks for any help!
-psixpsi

What partitions and/or OSs do you already have on that 160G drive?

---

### Post by psixpsi on 2008-03-12
initaially there was a vista partition and 47G of free space where i tried to install ubuntu.
i manually created 3G swap and the rest ext3 for the root. 
It failed when it started creating the / part. 
I came back to vista and cleared the space that 47G space again. 
Then ran LiveCD and instead of manual i let it take all free space.
The result was the same but it cleared vista as well.
Then few more attemps with alternate CD. 
After very long waiting same result---when it finally starts and
goes to creating partitions it fails and comes back to scanning the disks
detecting filesystems.
Now normal live CD does not run anymore, only alternate text-mode after very
long waiting. what the heck is going on????

---

### Post by mikeyphi on 2008-03-12
A couple of possibilities to look at:
How much RAM? you need 256min for Ubuntu
Did you burn the CDs? Sure there are no errors? CD drive OK?

And another thing - Check that your disk is not set as a RAID.

---

### Post by bodhi.zazen on 2008-03-12
If you are running vista, you should first partition your hard drive from within vista.

Sometimes your hard drive may be locked as well. See this blog :

[http://unlockforus.blogspot.com/2007/10/unlock-me-partitioning-your-drive-in.html](http://unlockforus.blogspot.com/2007/10/unlock-me-partitioning-your-drive-in.html)

---

### Post by psixpsi on 2008-03-12
liveCD is 100% ok, i've already successfully installed ubuntu from it.
memory is 1 or 2G.
now, after 25mins of waiting LiveCD (graphical) finally booted and i can
run fdisk. when i print the partition table it looks ok, shows correct filesystems.
how do i check if the disk is RAID??

thanks!!

---

### Post by psixpsi on 2008-03-12
> **bodhi.zazen said:**
> If you are running vista, you should first partition your hard drive from within vista.

Sometimes your hard drive may be locked as well. See this blog :

[http://unlockforus.blogspot.com/2007/10/unlock-me-partitioning-your-drive-in.html](http://unlockforus.blogspot.com/2007/10/unlock-me-partitioning-your-drive-in.html)

that's what i did--i cleared the space from vista.
now i recovered vista (it disappeared because
the bootable partition was set to a diff. one)
and it sees the linux partitions as healthy...
will take a look at the blog--thanks!

---

### Post by prshah on 2008-03-12
> **psixpsi said:**
> hi all!!

I/O Error on device sda3, logical block 8

thanks for any help!
-psixpsi


Disable "boot sector write protection" or "virus protection" or equivalent options in the BIOS.

To enter the BIOS, (usually) keep tapping DEL and F2 alternately when the computer is starting up... most Intel boards use F2, other use DEL...

Also, on a low mem machine, Xubuntu kept hiccuping until I booted using Safe Video Mode from the live CD...

---

### Post by psixpsi on 2008-03-12
thanks-will try that

meanwhile i got again the same message
after 5% of creating 37G /home

The ext3 file system creation in partition #4
of SCSI3 (0,0,0) (sda) failed

(headbang)

---

### Post by psixpsi on 2008-03-12
just checked the bios -- boot sector protection was disabled.
any ideas????
when i run fdisk after that failed partitioning with the installer
it shows the table as it should be...????

---

### Post by psixpsi on 2008-03-12
could it be a hardware problem, i.e. a faulty hdd?

thanks!

---

