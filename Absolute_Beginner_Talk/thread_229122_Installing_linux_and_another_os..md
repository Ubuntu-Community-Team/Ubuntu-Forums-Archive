---
title: "Installing linux and another os."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by vm_yap on 2006-08-04
Gud pm! 

1.) I have two separate hdds one has winxp and the other one has windows vista. what I want is on my second hdd which i already have a 40 gig partition that I used for windows vista which i will be formating it and replaced it with ubuntu. now can i do that?

2.) second ubuntu can't write on a ntfs but it can read files on it right?

3.) now do I have to partiton my 40 gig partition for swap files? (1 gig)

which file extension to use for linux

sorry its been awhile since i installed linux.

btw this is my hard drive chart
250 gb sata drive 2, partitioned into two: 30 gb for win xp and 200 gb for my files (i don't want to touch)

120 gb pata drive: 2 partitons: 40 gb for win vista (which i like to use for ubuntu) and 70 gb for downloaded softwares (this partiton cant be touch anymore because of the files in it.

and since i can't write on my ntfs drive can i partiton the 40 gb into two; 30gb/10gb, 10 gb on fat32 so that both os can write on it and then i'll just transfer my files on that partiton to my sata drive or to 70 gb partition, is this possible? or a 20gb/20gb will do?

other question:
is there ym for linux already (i'm not into gaim)

thank you.

---

### Post by rockfloyd on 2006-08-04
you can easily format the drive by downloading even a trial copy of BootIt NG. it's a boot floppy that lets you do all kinds of disk management.

yes ubuntu can read ntfs, and with tinkering it can write to it, but it's not recommended because of the way windows writes files.

yes you have to partition off a little chunk for swap, but it doesn't have to be big. mine is like 300 mb. it's definitely possible to partition your 40 gig drive to 30 as ext for linux and 10 as fat32 so both can read and write.

you might be able to run ym through wine. i don't know of one for linux.

---

### Post by vm_yap on 2006-08-04
thank you

---

### Post by vm_yap on 2006-08-04
hi again"

i'm gettingonfuse now, well its been awhile since i install one:

whats:

/
/home
/media

and if i choose /media the installer wont touch the partiton right?

---

### Post by cantormath on 2006-08-04
> **vm_yap said:**
> Gud pm! 

1.) I have two separate hdds one has winxp and the other one has windows vista. what I want is on my second hdd which i already have a 40 gig partition that I used for windows vista which i will be formating it and replaced it with ubuntu. now can i do that?

2.) second ubuntu can't write on a ntfs but it can read files on it right?

3.) now do I have to partiton my 40 gig partition for swap files? (1 gig)

which file extension to use for linux

sorry its been awhile since i installed linux.

btw this is my hard drive chart
250 gb sata drive 2, partitioned into two: 30 gb for win xp and 200 gb for my files (i don't want to touch)

120 gb pata drive: 2 partitons: 40 gb for win vista (which i like to use for ubuntu) and 70 gb for downloaded softwares (this partiton cant be touch anymore because of the files in it.

and since i can't write on my ntfs drive can i partiton the 40 gb into two; 30gb/10gb, 10 gb on fat32 so that both os can write on it and then i'll just transfer my files on that partiton to my sata drive or to 70 gb partition, is this possible? or a 20gb/20gb will do?

other question:
is there ym for linux already (i'm not into gaim)

thank you.

Im so glad I dont have to dual boot.

---

### Post by anaconda on 2006-08-04
Well actually..

You dont have to make an extra partition for swap. You can also make a swap file in your ubuntu partition after installing ubuntu. It is just as good as a separate partition.. 

And you dont have to make a separate fat32 partition for transferring files between windows and linux. IF you install ubuntu to ext3 partition, and install
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to your windows. Then you can read/write from/to your ubuntu partition from windows  without problems..

Actually it would be best if you could make your 70GB partition ext3 too.. but if you cant touch it..

---

### Post by vm_yap on 2006-08-04
ah i see,

so what "/" for

and for what i know /home is what i will choose to install linux on right?

---

### Post by anaconda on 2006-08-04
linux is installed to "/" If you dont choose any other (eg. /home /media etc..) then the whole filesystem goes to the same partition "/"

If you want you can define /home (or /boot /media or whatever) to be on a separate partition, but you dont have to.

Some people recommend to make /home a separate partition, but I dont... It is a matter of opinion really. Installation is easier if you put everything to 1 partition...

---

### Post by vm_yap on 2006-08-04
hi, thank you for the inputs and all that.

I still have some problems though:
1.) my sata 2 drive is mounted but cannot be access, it is a ntfs file system, 
2.) one partiton in my pata hdd which is ntfs file system cannont be access either,
3.)slow boradband internet in ubuntu, especially using automatix, and i still have 150 files to dl.. wah.. this also includes browsing the web, i disabled ipv6 (i think) but its still slow.
4.) how do i know if im using the root user? isnt it that i cant be login as admin all the time?

---

