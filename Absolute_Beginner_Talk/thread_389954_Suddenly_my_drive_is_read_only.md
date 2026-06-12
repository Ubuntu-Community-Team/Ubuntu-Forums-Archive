---
title: "Suddenly my drive is read only"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by datelus on 2007-03-21
hello. Could someone help me on this one?
i booted windows, and installed some drivers to read from my linux file system, and next time i boot it displays a lot of errors, saying that my filesystem is read only, and i cant write. i tried some commands with sudo, but still the same. any ideas?
[b]
edit: 
this really helped: 
sudo fsck /dev/hdb1

thanks a lot, people :)
[/b]

---

### Post by mrmonday on 2007-03-21
Do you mean linux or windows won't boot?

---

### Post by datelus on 2007-03-21
linux filesystem. now im stuck in win, searching for anserws

---

### Post by taurus on 2007-03-21
Maybe you need to boot from a LiveCD and fsck your root partition to see if there is any error.

Applications -> Accessories -> Terminal
```
sudo fsck /dev/hda2
```
Assuming /dev/hda2 is where / is resided.

---

### Post by datelus on 2007-03-21
i forgot to mention that, it does some forsed self check at start, and allways displays errors of some blocks.( lot of nummers ) then i press ctrl alt delete, it shows, that theres some error in my xserver, and i should fix it and than restart gdm. and in the middle you can see lot of :read-only filesystem errors. (cant write etc)

---

### Post by airtonix on 2007-03-21
does it drop you the terminal as root?

if so run the fsck as root ... you might have to do a couple of sweeps....reboot between each time.

moral of the story.....dont use ext readers for windows....go the other way round by using a ntfs-3g reader for linux to read your dozer partitions or setup a fat32 partition for use between both systems.

---

### Post by Nighto on 2007-03-21
the file system checker (fsck) of linux is slightly different of scandisk from windows, since it supposes that the currently user booting the system is *not* system admin (root) and thus not suited to know what to do when there are file inconsistances. so you need to log as root and check your filesystem (typing fsck) manually.

also check if your hd is ok, i have an old notebook that does exactly that from time to time because it's harddrive is defective :/

---

### Post by ril560 on 2007-03-27
Hey I'm having the same problem and fsck did not seem to help.

There was something about a last write time being in the future, but I clicked y to fix it and let fsck run its course. couldn't restart properly when it was done (apparently you have to have write capability to shutdown?) so i did a hard reset and started back up in recovery. Still the same problem. 

I still cant startx, shutdown, or create folders and files.

Any suggestions? If not I might have to make this a permanent windows box.

Thanks

EDIT: I just wanted to make it clear that i tried fsck from the hard drive not a live cd... would that change anything?

EDIT2: I just realized that my prompt no longer indicates my hostname ( root@(none) )

---

### Post by datelus on 2007-03-29
then maybe try from live cd.
sudo fsck /dev/hdb1*
where * is your disk, that has linux partition ,that wont boot.
to list all tables 
sudo fdisk -l

---

