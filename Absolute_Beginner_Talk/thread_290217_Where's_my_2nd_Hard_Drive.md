---
title: "Where's my 2nd Hard Drive?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-10-31
Hi Everyone,

I'm having trouble finding/using my second hard drive under :KS Kubuntu Edgy.  I have a 100GB drive set up as my primary one, and there's a 20GB "slave" drive in the box too.  When I installed Kubuntu, it asked me what to do with the drive and the default was a 20 gig "Swap" drive.  Being the default, I went with it, but now think that I've made the wrong choice.  

I basically want to have this drive set up for bittorrent, frostwire, etc.  Does anyone have any ideas getting it usable?  I'm actually pretty lost.

:-k

---

### Post by highneko on 2006-10-31
> **NewRubberSoul said:**
> Hi Everyone,

I'm having trouble finding/using my second hard drive under :KS Kubuntu Edgy.  I have a 100GB drive set up as my primary one, and there's a 20GB "slave" drive in the box too.  When I installed Kubuntu, it asked me what to do with the drive and the default was a 20 gig "Swap" drive.  Being the default, I went with it, but now think that I've made the wrong choice.  

I basically want to have this drive set up for bittorrent, frostwire, etc.  Does anyone have any ideas getting it usable?  I'm actually pretty lost.

:-k
I'm very tired, I think I understand. Maybe type "df -hT" and paste the results?

---

### Post by NewRubberSoul on 2006-10-31
It looks like this doesn't mention the second hard drive.. 

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     91G  7.0G   79G   9% /
varrun       tmpfs    252M   96K  252M   1% /var/run
varlock      tmpfs    252M     0  252M   0% /var/lock
procbususb   usbfs     10M  148K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  148K  9.9M   2% /dev
devshm       tmpfs    252M     0  252M   0% /dev/shm
lrm          tmpfs    252M   18M  235M   7% /lib/modules/2.6.17-10-generic/volatile

```

---

### Post by tubasoldier on 2006-10-31
LOL, 20GB Swap. wow, you would never use that.

Basically your second hard drive is mounted as /swap.
what does this mean?
It means that you have 20 gb of backup memory. 20GB of space for when your ram runs a little low.

I would reccomend using gparted to visually see whats going on. Also re-installing with your root partition: / on the 20GB with about 512mb of swap on that drive as well would work well. then your 100GB drive mount it as /home.  Thats the best solution I could think of for your situation.

Linux does not give hard drives names like Windows does. Linux gives the hard drive a place. that place is a mount point.

---

### Post by NewRubberSoul on 2006-10-31
Thanks for the advice.  I know that the install made a separate swap partition of about 512MB or so... so it looks like two swap drives.  Sounded funny to me too...

So you think I should install gparted instead of using the kde version?  Would that actually be better?

---

### Post by highneko on 2006-10-31
Edit; nevermind, he's right. You could recreate the swap and Data filesyetem without reformat. i don't remember how it's done. I don't wanna find out. Good luck.

---

### Post by tubasoldier on 2006-10-31
After looking at your hard drive print out I see a lot of very small partitions that probably will not suit you too well. Here is my reccomendation:

20GB Drive
/  -Root partition. Make it about 19.5GB
/swap   Your swap space. It is utilized when your ram runs low.  Make it about 512mb.

100GB Drive
/home

Basically if this is a fresh install I think your better off to do it again.

---

### Post by NewRubberSoul on 2006-10-31
Thanks for all the great advice so far, I think I'm close to understanding what to do.  But how to go about doing it?  Gparted you think?  Or is there a good KDE equivalent?

---

### Post by tubasoldier on 2006-10-31
> **NewRubberSoul said:**
> Thanks for all the great advice so far, I think I'm close to understanding what to do.  But how to go about doing it?  Gparted you think?  Or is there a good KDE equivalent?

Qtparted will work as well. the "KDE equivalent".   But it is in my experience that gparted has a simpler and nicer interface. And if you have gimp installed then you have most libraries to run it installed anyways.

---

### Post by NewRubberSoul on 2006-10-31
I know I'm being a total noob, but I installed gparted and now can't use any of the features.  The 19.5 gb "Swap" show up, but all of the features are disabled and there's a big lock icon next to it.  

Sorry for the "baby steps" approach.

---

### Post by tubasoldier on 2006-10-31
> **NewRubberSoul said:**
> Sorry for the "baby steps" approach.

Baby steps are fine. The reason you can not do anything to your disk is because it is "in use".  It is like your root /.  You can not do anything to it because it would damage your disk if you did. In the file /etc/fstab you will be able to find a reference to it. You would have to remove that reference and save the file. Then becuase you are so new to linux I would reccomend just restarting your system. Removing this reference will ensure that it is not mounted at boot time. Then you can mount it into whatever directory you want.

---

