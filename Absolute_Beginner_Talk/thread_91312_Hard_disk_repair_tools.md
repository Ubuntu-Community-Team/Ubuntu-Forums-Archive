---
title: "Hard disk repair tools"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by BobSongs on 2005-11-16
Greetings;

Well, I made the plunge. Edubuntu is installed on my 2nd PC and I've got a friend who'll dual boot Edubuntu and WindowsXP Pro.

While booting his PC to do some further tweaking I noticed a message in text mode that complained about inodes and whatnot. I can't tell you what it said. But I thought this would be a good point to ask the community (and a very helpful community it appears to be!) what we have in the way of hard disk tools. Something that might compare to 'chkdsk' in the Win/DOS world.

The message hasn't repeated itself. So I can't replicate it (eww, intermittent errors: the worst kind) or tell you how it occurred.

As to what file system it is, I just wiped the entire partition by selecting the default 'wipe and install' during the basic set up.

I'll be glad to answer any questions. But I would like to check to see if the file system is up to scratch. Or at least know if the system checks itself out and makes corrections appropriately.

Bob

---

### Post by Kyral on 2005-11-16
Its prolly EXT3. Unmount the drive and run

```
sudo fsck.ext3 <device>
```

---

### Post by BobSongs on 2005-11-16
Thanks, Kyral!

See? An impressive forum. I'll try unmounting the drive: umount, I believe. Anyways, if the system catches fire or nuts and bolts fly out at lightening speed, I'll post an update.

Thanks again!

Bob

---

### Post by steve.horsley on 2005-11-17
The trouble is, the error is probably on your root partition, which you can't unmount. You probably need to fire up a live CD (Ubuntu, knoppix, whatever) and run fsck from there. BTW, fsck is short for File System ChecK.

---

### Post by sjh on 2005-11-18
[QUOTE=steve.horsley]The trouble is, the error is probably on your root partition, which you can't unmount. You probably need to fire up a live CD (Ubuntu, knoppix, whatever) and run fsck from there. BTW, fsck is short for File System ChecK.[/QUOTE]


I would go with Knoppix and use this site as a guide
[http://www-128.ibm.com/developerworks/linux/library/l-knopx.html?ca=dgr-lnxw82KNOPPIX](http://www-128.ibm.com/developerworks/linux/library/l-knopx.html?ca=dgr-lnxw82KNOPPIX)

SJH

---

### Post by BobSongs on 2005-11-18
Yep. Noticed that. So I used a Slax Live CD. But the 'fsck' complained about the ext2 partition. So, I didn't go any further. (I think the drive is ext3, not 2.)

I wondered about how I could possibly unmount the current drive and still have access to tools. :???:  Figured there was something Linux might be able to do that simply bordered on magic.

But eventually I realised that unmounting the primary (and only) drive would be a bit weird. I mean: a DOS boot diskette can be remove from A: drive and still function, as long as it doesn't need to access 'command.com' or another binary like 'xcopy.com'. I just figured Linux would do the same. #-o

Thanks for the advice. The PC is in its owners hands. I'm sure I'm going to get a few questions which I'll ask along the way.

(Off topic: my kids really like Edubuntu above other tested distributions of GNU/Linux.)

---

### Post by Kyral on 2005-11-18
If you need to check your root FS then the best way is to boot from a LiveCD and run the fscks from there (they are pretty much standard equipment)

---

