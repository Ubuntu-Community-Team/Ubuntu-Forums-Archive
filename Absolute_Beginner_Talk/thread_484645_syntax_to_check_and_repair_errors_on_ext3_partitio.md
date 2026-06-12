---
title: "syntax to check and repair errors on ext3 partition"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-06-26
so i went out, bought me a snazzy 320gig external usb hard drive. put a metric buttload of stuff on it... have it set up in fstab to mount at /data/video... everythings going gravy. Well not so gravy.

randomly when i boot up (though way more frequently now than i like) it says the filesystem has errors and needs to be checked, wich it does and finally scrolls passed the results and lets me continue booting

as this is happening more and more frequently, any ideas what would have caused the errors, how to find out what these errors are, and how to fix them... fsck on 200gigs of data at every boot is very time consuming... and i fear for my data... would like to get this fixed without losing that much info, but if needs be im willing to completely wipe the partition in an attempt to fix whatever errors its experiencing

i have read man pages on fsck, e2fsck and fsck.ext3 (wich is just the man page for e2fsck) but all the options and flags and arguments get very difficult to sort through, and im a little afraid of jacking up and damaging the partition even more so anyone without advice on the proper syntax to scan for errors and fix them without destroying data would be greatly appreciated

---

### Post by yabbadabbadont on 2007-06-26
Are you making sure that you unmount the drive before unplugging it?  You shouldn't have to, but you might even want to unmount it manually before shutting down.

---

### Post by kenweill on 2007-06-26
I too have experienced that kind of problem. But its on Ubuntu 6.10. And because of it, i get stuck on loading gnome. Or takes too long to load gnome.

And its the reason why i kept coming back to Dapper.
On Dapper, i just issue the command "sudo shutdown -rF now"... It automatically shutdowns and force to run fsck on reboot. I tried the same command but its not working on 6.10 anymore. There's no more "F" option, or force fsck check.

---

### Post by Nythain on 2007-06-26
i am now... and i think the few time i didnt along with defaults in the fstab (wich async instead of sync conserned me) might have been what caused the errors...

i eventually ran fsck -C /dev/sdc1 -- -p and after about a half hour scan, it returned 2.2% non-contigous... and im assuming it repaired what it could since every fsck after that has reported clean...

i have now edited my shutdown.sh to include a /bin/umount /data/video hopefully that should work

any clue if eject would be better than umount for this purpose, and how to go about using eject, everytime i try a sudo eject -s /dev/sdc1 it returns this error
eject: unmount of '/data/video' failed

---

### Post by yabbadabbadont on 2007-06-26
> **kenweill said:**
> I too have experienced that kind of problem. But its on Ubuntu 6.10. And because of it, i get stuck on loading gnome. Or takes too long to load gnome.

And its the reason why i kept coming back to Dapper.
On Dapper, i just issue the command "sudo shutdown -rF now"... It automatically shutdowns and force to run fsck on reboot. I tried the same command but its not working on 6.10 anymore. There's no more "F" option, or force fsck check.

Create a file called "forcefsck" in the root directory of the filesystem you wish to be checked on next boot.  As an example, I have a separate partition for /home.  If I wanted to force it to be checked on next boot, I would in a terminal run:
```
sudo touch /home/forcefsck
```

---

### Post by yabbadabbadont on 2007-06-26
> **Nythain said:**
> i am now... and i think the few time i didnt along with defaults in the fstab (wich async instead of sync conserned me) might have been what caused the errors...

i eventually ran fsck -C /dev/sdc1 -- -p and after about a half hour scan, it returned 2.2% non-contigous... and im assuming it repaired what it could since every fsck after that has reported clean...

i have now edited my shutdown.sh to include a /bin/umount /data/video hopefully that should work

any clue if eject would be better than umount for this purpose, and how to go about using eject, everytime i try a sudo eject -s /dev/sdc1 it returns this error
eject: unmount of '/data/video' failed

As long as you do a normal shutdown, it should have been unmounted properly.  It should have only become corrupted if you unplugged the USB cable, or turned the drive off, without right-clicking and ejecting it (which does a umount on it), or running "sudo umount /data/video".

---

### Post by Nythain on 2007-06-26
bum... never unplugged it... just regular old shutdowns, wich i figured would unmount it, since it has to unmount every filesystem in the process... oh well... hopefully we'll see if the fstab edits help... thanks for the ideas

---

### Post by kenweill on 2007-06-28
> **yabbadabbadont said:**
> Create a file called "forcefsck" in the root directory of the filesystem you wish to be checked on next boot.  As an example, I have a separate partition for /home.  If I wanted to force it to be checked on next boot, I would in a terminal run:
```
sudo touch /home/forcefsck
```

Thanx alot man. It works. It works both on dapper and on 6.10.
Im back in 6.10. Still waiting for the 7.04 cds from ShipIt. Until now, I haven't receive any. Its approved in Shipit but haven't received it yet.

---

