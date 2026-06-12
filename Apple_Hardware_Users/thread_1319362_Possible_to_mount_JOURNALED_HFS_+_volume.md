---
title: "Possible to mount JOURNALED HFS_+ volume?"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by RickyBobby on 2009-11-08
Hi all, in my various searchings I've found some ideas on how to mount HFS+ volumes within Ubuntu, but most insist on disabling journaling for it to work.  The thing is, my Mac had died on me (video card I think), so I'm unable to turn off journaling.  I've got the HD from the Mac in an external enclosure, and had limited success mounting it from my Ubuntu laptop, no success getting write-access to it, and finally I couldn't mount it at all.  I wasn't clear if more recent versions of Ubuntu might be able to handle the journaling.  I'm running 9.04.

The Mac is well out of warranty and I'm not optimistic a repair will be cost effective, but was hoping to salvage the drive.  May end up just replacing the Mac which would solve my problem.

---

### Post by oswaldkelso on 2009-11-08
If my memory serves me right you can do it from the command line. Sorry I could'nt find the gnu/linux info. Only osx  [http://castyour.net/node/40](http://castyour.net/node/40) it should give you the idea

edit: look at formatting ipods for rockbox I'm sure I saw a how to that will give you some clues

---

### Post by oswaldkelso on 2009-11-08
[http://art.ubuntuforums.org/showthread.php?t=392287&](http://art.ubuntuforums.org/showthread.php?t=392287&)

---

### Post by RickyBobby on 2009-11-08
Thanks, but as I said my mac is dead; I still don't see how to turn off journaling when i don't have access to the Mac.

---

### Post by oswaldkelso on 2009-11-09
Sorry it was late. 
  The only way to turn off journalling as far as I know is from OSX. If you can boot an OSX install CD/DVD you can do it from there?
If you have firewire connection on your ext-HD or dead machine. You can boot in target disk mode from any other mac to turn it off.

It maybe possible from open firmware. Depending how dead your machine is.

Just to be clear it should be easy to mount it from Ubuntu you just can't get your data off HFS-PLUS.

---

### Post by tuwe on 2009-11-09
if journaling is enabled on the hfsplus partition, you can only mount it read-only in linux.

for example:
```
sudo mkdir /media/OSX
sudo mount -t /dev/sda2 /media/OSX
```

make sure you mount the correct partition though.
you can then access all data on the hfsplus partition. you probably need to do this with sudo since hfsplus has its file permissions set according to OS X's own permission table, i.e. the normal user has uid 501 and gid 20 and so on.

---

### Post by RickyBobby on 2009-11-09
I think the video card on the mac is fried and the screen is all scrambled, so I can't operate disk utility or boot up from a cd.  I'm probably going to get another mac, unless this one can be repaired. Thanks for your help!

---

