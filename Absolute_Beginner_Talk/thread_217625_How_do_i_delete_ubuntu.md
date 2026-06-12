---
title: "How do i delete ubuntu?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by mech7 on 2006-07-17
How can I remove Ubuntu and grub and turn it back into a normal NTFS partition again.. So that I boot with XP pro again

It was fun to play around but im kinda tired of dual booting and Ubuntu kinda lacks in certain areas i think :-k

---

### Post by uzi09 on 2006-07-17
you probably partitioned your hdd for this. so you'll have to basically wipe out the partitions for ubuntu and extend the ntfs partition to take up the whole disk.

you should be able to wipe out the partitions using the ubuntu install cd. to extend partitions, use the "system rescue cd" (get it here [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) to run qtparted (partition magic look-alike) to resize the ntfs partition.

ps: if you ever just want to try out a distro, most distro's have "Live CDs" available where you can get your system to boot off a cd without making any changes to your harddrive. save you a lot of hassle :D

---

### Post by mech7 on 2006-07-17
So if I delete the entire ubuntu partition everything should be ok? and the grub loader is gone too ?

---

### Post by MaximB on 2006-07-17
after deleting the partition you will have to restore "winxp boot"
just put your winxp cd - boot from it and make a restoration.

---

### Post by confused57 on 2006-07-17
> **mech7 said:**
> So if I delete the entire ubuntu partition everything should be ok? and the grub loader is gone too ?

No, I believe the grub boot loader will still be there.  Don't do anything yet...I'm not sure, but I think your best course of action would be to bootup with the Windows Install CD(a Windows Recovery CD won't work), press "r" to enter recovery mode, then enter   fixmbr    
This will restore the Windows mbr, so that you can bootup Windows but you won't be able to boot Ubuntu.  Then you can use the instructions by uzi09 to delete the Ubuntu partition and resize your NTFS partition.
I don't know for sure, haven't done it myself; but it might be the best way to go about it.
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=211169&highlight=uninstall+ubuntu](http://www.ubuntuforums.org/showthread.php?t=211169&highlight=uninstall+ubuntu)

---

### Post by mech7 on 2006-07-17
seems to work ok.. just needed to do fixmbr and deleted from windows disk managent :)

---

