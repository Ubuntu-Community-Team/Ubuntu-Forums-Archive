---
title: "i made a mess with my partitions... help (:"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-10-16
well, long story short: i had 3 partitions(from now on aka par): 
c - windows - NTFS 1 gig available
x - ubuntu - fat32
d - my music and stuff - fat32

now, i had to extract a 4.5 gig file, so in order to do that i had to make another NTFS par
i did it via Windows
then i had the Grub 17 error
so i reinstalled ubuntu
and now everything is fine

But

my new NTFS par is recognized by Ubuntu, but since i have no permissions for this par, i cant extract the file into it
so i tried to login to my Windows.
and the par isn't there...

appreciate your help (:

---

### Post by santiagoward2000 on 2007-10-16
Hi asakurax,
There's one thing I'm not sure about. You said you installed Ubuntu on a Fat32 partition, but Ubuntu uses ext3 as format (which can't be recognized by Windows).
To copy things on Ubuntu to the NTFS partition you could just open the file manager as sudo. Just type:
```
sudo nautilus
```
On a console. Just be carefull you don't mess with any system files.

---

### Post by asakurax on 2007-10-16
right, my bad
my Ubuntu is ext3 or 2 cant really remember...

umm the problem is that i cant copy the file, because in the first place i cant extract it to the Fat32 par...

i just cant understand why i dont have permission to the NTFS par

---

### Post by santiagoward2000 on 2007-10-16
I don't know why you can't extract it to the FAT32 partition, I never had problems with it. About the NTFS, Ubuntu doesn't give you the privileges, probably to avoid messing up with Windows. I thought you could access it if you used sudo, but I just tried and I couldn't :(
Sorry

---

### Post by fluffman86 on 2007-10-16
You need to enable ntfs-3g in Feisty, or use gutsy.  This will give you write permissions to your NTFS drive.

Google or search here for a HOWTO.

---

### Post by asakurax on 2007-10-17
> **santiagoward2000 said:**
> I don't know why you can't extract it to the FAT32 partition, I never had problems with it. About the NTFS, Ubuntu doesn't give you the privileges, probably to avoid messing up with Windows. I thought you could access it if you used sudo, but I just tried and I couldn't :(
Sorry

FAT32 cant contain files bigger than 4 gig
my file is 4.5

> **fluffman86 said:**
> You need to enable ntfs-3g in Feisty, or use gutsy.  This will give you write permissions to your NTFS drive.

Google or search here for a HOWTO.

wow, i totally forgot about this program

thx (:

Edit: i downloaded the NTFS configuration tool
there are two boxes to mark in it: internal and external
but the internal one is gray.... as in cannot be marked...

---

### Post by GlennW on 2007-10-17
This is really my thread title too!! I really made a mess of it as well. I was a bit desperate to get 7.04 up and running (after I totally screwed up kernel modules) so that I could upgrade to 7.10. I read through piles of the forums and came across someone with a similar issue and was given the advice to delete the partition which held 7.04. That's just great, however, now I have Grub error 17. I cannot boot to xp (dual boot) and cannot get to 7.04 unless I boot off the CD. 

I so love Ubuntu and I can hardly wait for 7.10!! 

What can I do to get past the Grub 17 error?

---

### Post by bigboy_pdb on 2007-10-17
GlennW, if all you did was delete the partition then the space is still there. You can just re-install Ubuntu using the free space from the CD.

---

