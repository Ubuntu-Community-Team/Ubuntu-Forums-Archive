---
title: "How do I format in ubuntu 7.04?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by genji_ on 2007-10-02
Hey guys, complete linux newbie here :D

I took a  160GB harddrive from my other pc and put it in my ubuntu box. The thing is I have allot of junk on it and I would really like to delete all that stuff :s

Can anyone tell me how to do this?

---

### Post by charles.g.moore on 2007-10-02
> **genji_ said:**
> Hey guys, complete linux newbie here :D

I took a  160GB harddrive from my other pc and put it in my ubuntu box. The thing is I have allot of junk on it and I would really like to delete all that stuff :s

Can anyone tell me how to do this?

I know that in Dapper I can mount the drive (which it sounds like you already did)
System>administration>disks and there is an option in there to format a drive...

---

### Post by genji_ on 2007-10-02
hmm, there is no disks when i go to system > administration >           

1 more thing, what file system do you recommend me formatting it to? ntfs or ext3? I'm going to use the my windows XP main pc to  to send/receive files from my linux box(movies/mp3s etc).

---

### Post by logos34 on 2007-10-02
system>admin>gnome partition editor

if not there install it:

sudo apt-get install gparted

choose drive upper right

unmount partition(s)

delete

'New' partition -->make primary ext3

> 1 more thing, what file system do you recommend me formatting it to? ntfs or ext3? I'm going to use the my windows XP main pc to to send/receive files from my linux box(movies/mp3s etc).

get fs-driver so windows can r+w access ext2/3

---

### Post by 3rdalbum on 2007-10-02
For security reasons, I would advise doing it the opposite way; rather than format as Ext3 and install an Ext3 driver for Windows; I would format the disk as NTFS and install NTFS-3G. The performance won't be as good, but it will be better from a security standpoint.

---

### Post by genji_ on 2007-10-02
Thanks allot guys, formatting atm =)

---

### Post by dptxp on 2007-10-02
> **3rdalbum said:**
> For security reasons, I would advise doing it the opposite way; rather than format as Ext3 and install an Ext3 driver for Windows; I would format the disk as NTFS and install NTFS-3G. The performance won't be as good, but it will be better from a security standpoint.

Yes, Windows should not write to ext3, the Linux root should be safe.

---

### Post by genji_ on 2007-10-02
Hey i formatted it to ext3 because i'm not really concerned about security on this harddrive. 
The problem i have now is that i can't create files/folders in the new disk :( 

Can anyone help me out real quick?

---

### Post by dptxp on 2007-10-03
> **genji_ said:**
> Hey i formatted it to ext3 because i'm not really concerned about security on this harddrive. 
The problem i have now is that i can't create files/folders in the new disk :( 

Can anyone help me out real quick?

You have to mount it.

---

### Post by genji_ on 2007-10-03
> **dptxp said:**
> You have to mount it.

that's not all, you have to do some other stuff too.

eph1973 explained it in the other thread of mine =)

---

