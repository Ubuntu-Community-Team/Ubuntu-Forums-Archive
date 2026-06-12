---
title: "unmounting an ubuntu hard drive"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-05
Hello forum.

please can you help me sort out some hard drive questions.

I have a very standard hard drive partition set up in ubuntu...same as is shown below...(similar sizes)

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

i want to do exactly what the person above has done..

i want to shrink my /dev/hda drive from 36 gigs to around 26 gigs....leaving me 10 gigs of unallocated space....then i want to make a new partition in that space of 10 gigs in size...

it's not possible to do any of the above in Gparted until my existing drive arrangement has been unmounted...

please can you tell me what command to use and what to unmount before i use Gparted...

After i have used Gparted correctly, please can you tell me the commands i need to use to mount my new arrangement of partitions/drives back up and running.

thanks

Vince.

---

### Post by ruy_lopez on 2008-04-05
The simplest method is to use the LiveCD. The LiveCD doesn't automatically mount partitions. Plus it has Gparted.

I've unmounted a drive while booted into Ubuntu before. But the last time I tried, I got a "device busy" message.

---

### Post by mikeyphi on 2008-04-05
In order to access your drive for resizing it needs to be taken "off-line" so to speak. This can't be done if you are trying to use gparted from inside the OS. You need to use a LiveCD (or a CD copy of gparted) so that you are not "using" the hard drive.

So - run an 'external' copy of gparted and then unmount (or check it's unmounted) your drive and go ahead with the resize.
Good luck! - Don't forget to back up important data in case there's a problem!!!

---

### Post by vinceUUUU on 2008-04-05
Hello,

thanks for the reply.

yes, i had to go the store and get some blank CD discs....so i can now make a live CD of Gparted and use it...

thanks

Vince.

---

