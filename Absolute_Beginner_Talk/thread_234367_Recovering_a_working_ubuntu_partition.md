---
title: "Recovering a working ubuntu partition"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by F3rrum on 2006-08-11
So I built a new computer (#1) and decided to reuse a hard drive from another computer (#2). In #2 I had 2 harddrives with win2k installed on the first one (hd1) and two partitions on the second hard drive: a windows partition and a complete ubuntu partition (dapper drake). Grub was installed on hd1

So in #1 I put in hd2 and reinstalled windows on the existing windows partition. All fine. Now I am trying to use the dapper livecd to install grub so I can boot both the newly formatted windows and the pre-existing ubuntu. However the trick of getting grub to install by starting a fresh ubuntu install process isn't working (fyi the ubuntu partition has about 1 gig of space left so am not just able to do a full reinstall since it says not enough space and hangs the installer). I am also not able to do grub-install since it says it can't find /boot. 

I am thinking that perhaps I can just free up some space on the ubuntu partition and do a reinstall but I dont know how to mount the partition so that the livecd lets me delete stuff.

Best case I would like to just install grub and not hafta go the free up space and needlessly reinstall dapper route since it is already there.

Thanks

---

### Post by tehnad on 2006-08-11
To install grub back into the MBR type this in a terminal of your live cd:
```
sudo grub
root (hdx,x)
setup (hdx)
quit
```

Replace the X's with your device that you want grub installed on.

To answer your other question, if you were to do a install again for what ever reason, all you need to do is go to System>Administration> and look for the gnome partition editor that is on lthe live disk.  It will wipe the partition you want clean and will allow you a complete fresh install.

---

### Post by FenrisAbraxas on 2006-08-11
> **F3rrum said:**
> So I built a new computer (#1) and decided to reuse a hard drive from another computer (#2). In #2 I had 2 harddrives with win2k installed on the first one (hd1) and two partitions on the second hard drive: a windows partition and a complete ubuntu partition (dapper drake). Grub was installed on hd1

So in #1 I put in hd2 and reinstalled windows on the existing windows partition. All fine. Now I am trying to use the dapper livecd to install grub so I can boot both the newly formatted windows and the pre-existing ubuntu. However the trick of getting grub to install by starting a fresh ubuntu install process isn't working (fyi the ubuntu partition has about 1 gig of space left so am not just able to do a full reinstall since it says not enough space and hangs the installer). I am also not able to do grub-install since it says it can't find /boot. 

I am thinking that perhaps I can just free up some space on the ubuntu partition and do a reinstall but I dont know how to mount the partition so that the livecd lets me delete stuff.

Best case I would like to just install grub and not hafta go the free up space and needlessly reinstall dapper route since it is already there.

Thanks

I think it's highly recomended you reinstall for hardware issues.

To mount the partition from the live cd do this:
```

sudo -s -H (to stay at root)
mkdir /media/ubuntuTemp
mount /dev/hdXY /media/ubuntuTemp <-- adjust to match your hardrive

```

That will mount the partition in ubuntuTemp there you should be able to backup all your data to some other partition.

---

