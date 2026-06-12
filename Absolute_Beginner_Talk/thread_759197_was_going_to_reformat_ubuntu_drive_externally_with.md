---
title: "was going to reformat ubuntu drive externally with windows"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by bm13084 on 2008-04-18
but windows didnt see the drive.

i pulled up the drive manager or whatever and deleted the main partition, thinking it would at least get windows to recognize the hard drive (i was planning on putting windows back on the drive first, anyhow).

Basically, now the drive isnt working right back in the laptop i pulled it from.  

im such an idiot.


anyhow, im assuming i can somehow get windows to see that drive with the usb enclosure again, somehow... right? whats the way to do that?

---

### Post by northern lights on 2008-04-18
You were only going to format?!

Then just do so, with the drive in the laptop, using one of the following ways:

1. You meant to install Windows on it? Boot from the Windows setup CD and format the drive before installation from there.

2. Run any Ubuntu installation and format the drive during the course of the setup process.

3. Boot from Ubuntu (or any other) LiveCD and format from there...

---

### Post by bm13084 on 2008-04-18
for some reason grub gives me errors (17 i believe) when i run the harddrive.

and then the live cd just hung up...

---

### Post by northern lights on 2008-04-18
Of course GRUB will give you errors if you tampered with the partition table.

In your BIOS, set the CD drive as the only / first boot device, pop in the LiveCD - off you go.

---

### Post by bm13084 on 2008-04-18
Like I said, the live cd is hanging up when i boot from it.


i have the hard drive back in my desktop and am trying to use partition magic... that program sees the drive, but windows doesnt... i cant figure out what to do about that...

---

### Post by northern lights on 2008-04-18
> **bm13084 said:**
> partition magic [...] sees the drive, but windows doesnt

Fair enough. In PM, delete all partitions (of that drive!) and reformat as NTFS - Windows will "see" it...

---

### Post by bm13084 on 2008-04-18
maybe it's because it's a demo version, but it seems to not do anything when i click apply.

they all go back to being three partitions and [*] as the name.



this is driving me nuts.... is there another program i can use?

---

### Post by erlyrisa on 2008-04-18
I here your grief .... it used to be so easy in the old days.

Fdisk is useless for Usb drive ... so yeah under windows there is no "command" to format.


--go to

Control Panel
Administrative tasks
Computer manegement
Harddisks
-
your drive should be listed their - you will be able to delete the partition and format it.

Just note that you are deleteing the RIGHT ONE>

---

### Post by bm13084 on 2008-04-18
well, i got one of my live ubuntu's to load... it's got an error (according to the error that popped up during partitioning)

but i figure if it's partitioning, i can use it to do a clean install tomorrow... as long as my cd isnt corrupt.

---

