---
title: "Cannot write to HFS+ journaled"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by stevebush on 2009-02-14
My Leopard partition is messed up as some kext files were misplaced and I used the Ubuntu Live disk to access the partition to repair it. However, I can only read the partition and cannot write to it.

Some help would be great.

---

### Post by mkvnmtr on 2009-02-14
I don't believe there is support to write to journeled mac files. Maybe you could remove the files to a usb stick formated extended and rewrite them there and then put them back. You might also need to search the three cross platform sections in the package manager for apps to help you deal with mac files.

---

### Post by damis648 on 2009-02-14
Sorry, the current state HFS+ driver cannot write to Journaled volumes. Can you boot up in single user mode (Cmd+S at boot)? If you can, just do
```
mount -uw /
diskutil disableJournal
reboot
```
and then pop the Ubuntu CD in and you should be able to write to the partition with the LiveCD. Cheers!:popcorn:

---

### Post by stevebush on 2009-02-15
I cannot load the OS as there is an issue with system files which I need to repair using the Live CD.

Anyways, can you suggest me other Live CD that can allow me to write to HFS+ Journaled.

I don't mind downloading it an burning it to repair my Mac.

---

### Post by damis648 on 2009-02-15
> **stevebush said:**
> I cannot load the OS as there is an issue with system files which I need to repair using the Live CD.

Anyways, can you suggest me other Live CD that can allow me to write to HFS+ Journaled.

I don't mind downloading it an burning it to repair my Mac.

Sorry, the HFS+ driver that all distros use is more or less the same and can not write to journaled partitions. Do you have an OS X DVD? Try booting that up and then go to Utilities > Terminal and see if
```
diskutil disableJournal /dev/rdisk0
```
works.

---

### Post by stevebush on 2009-02-15
> **damis648 said:**
> Sorry, the HFS+ driver that all distros use is more or less the same and can not write to journaled partitions. Do you have an OS X DVD? Try booting that up and then go to Utilities > Terminal and see if
```
diskutil disableJournal /dev/rdisk0
```
works.

Thanks a lot. You are a lifesaver !! :)

I replaced the system files and my Mac works like before! This would not have been possible without you!


___

SOLVED.

---

### Post by damis648 on 2009-02-15
> **stevebush said:**
> Thanks a lot. You are a lifesaver !! :)

I replaced the system files and my Mac works like before! This would not have been possible without you!


___

SOLVED.

No problem! Glad to have helped, cheers! :popcorn:

---

### Post by ktran03 on 2009-02-15
i got the same problem....

will try this when i get home.

---

### Post by nolongeriprocs on 2009-02-15
got the same problem :(

---

