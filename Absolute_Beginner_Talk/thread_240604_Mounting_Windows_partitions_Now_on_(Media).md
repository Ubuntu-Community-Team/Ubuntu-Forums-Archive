---
title: "Mounting Windows partitions Now on (Media)"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-08-21
When I installed Ubuntu for some reason the Win XP partitions were auto mounted in Media and they have icons on the desktop. I read somewhere that they should not be mounted in Media. Can someone advise why it is not advised to mount in Media and how I mount them somewhere else so I can access the drives. I have four partitions on one disk /dev/sda1,5,6,7 all NTFS and two parts on the same disk as Ubuntu /dev/sdb6,7 both NTFS](*,) 
My vfat32 part for Ubuntu sdb5 also has an icon on the desktop. Is this correct setting up of the partitions and correct mounting

---

### Post by xpod on 2006-08-21
Thats where i got my xp mounted and i believe thats the place to have it if you want it to show on the desktop...Nothing wrong with it being mounted in /media as far as i know........

---

### Post by whatrucrazy on 2006-08-21
i have done installs with XP partitions mounted throught /media/ and had no problems, also with a second hard drive (hdb1 ext3) mounted through /media/ and had no issues with that either.

are there any particular issues you are wondering about?

if you do want to mount them somewhere else you can edit your fstab file to make it automount wherever you want. there are plenty of howto's for this on the forum, just folow the instruction and yopu won't have any problems, its not that hard.

---

### Post by xpod on 2006-08-21
Im just curious as to how it was pre-mounted.........I had to do all the MKDIR and FSTAB stuff first?

---

### Post by Gerry Atric on 2006-08-21
Just having read somewhere online that XP part or NTFS should not be mounted in Media I wanted to make sure that I was doing the right thing. Thanks for your re-assurance much appreciated

---

### Post by Gerry Atric on 2006-08-21
I dont actually know how it became pre-mounted, when I installed Ubuntu it was set up. I played no part is mounting the drives they just appeared as icons on the desktop and worked fine right from the start. I am totally new to Linux and Ubuntu so didn't think anything of it until I read online somewhere that they should not be mounted on Media. Think I am doing too much reading about Ubuntu Dapper online, maybe I'd better give it a rest for a while.:rolleyes:

---

