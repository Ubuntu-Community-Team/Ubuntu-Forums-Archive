---
title: "stopping fsck at booting"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by XProgrammer on 2007-04-13
[FONT="Georgia"]

[SIZE="4"]

Hi All,

I've ext3 drive with size of 13GB. While booting, fsck takes quit sometime to do its job on that partition. I would like to stop doing fsck at boottime. Is that harmful to system ?. and How can i stop fsck while booting.

Thanks in advance,

Regards,
XProgrammer


[/SIZE]
[/FONT]

---

### Post by stalker145 on 2007-04-13
> **XProgrammer said:**
> How can i stop fsck while booting.

I'm not quite sure why you'd want to stop fsck. It only runs every 30 or so boots by default. I have a 60 and a 40GiB HDD on my two computers and the one time it runs every month or so only takes *maybe* 2 or 3 extra minutes. To me, it's worth it to make sure that my file system is stable.

To answer your question: I'm sorry, I don't know. You *can* search the forums as I've seen several different threads asking a similar question.

[http://ubuntuforums.org/showthread.php?t=401976&highlight=stop+fsck](http://ubuntuforums.org/showthread.php?t=401976&highlight=stop+fsck)
[http://ubuntuforums.org/showthread.php?t=390126&highlight=stop+fsck](http://ubuntuforums.org/showthread.php?t=390126&highlight=stop+fsck)
[http://ubuntuforums.org/showthread.php?t=195620&highlight=stop+fsck](http://ubuntuforums.org/showthread.php?t=195620&highlight=stop+fsck)

---

### Post by Bob Unitt on 2007-04-13
> **XProgrammer said:**
> [FONT="Georgia"]
I've ext3 drive with size of 13GB. While booting, fsck takes quit sometime to do its job on that partition. I would like to stop doing fsck at boottime. Is that harmful to system ?. and How can i stop fsck while booting.
[/FONT]

AFAIK this should only happen every 30 boots - if it's happening on every boot I suspect you have a problem with your hard-disk.

Anyway, to stop it happening on your next boot open a terminal and run :-

[FONT="Courier New"] [SIZE="3"]     sudo touch /fastboot[/SIZE][/FONT]

Note that you will need to re-run this after every boot.

---

### Post by pistcivet on 2007-04-13
The program used to "adjust tunable filesystem parameters on ext2/ext3 filesystems" is:
tune2fs

Never used it though. maybe try:```
man tune2fs
```
Good luck! :)

---

