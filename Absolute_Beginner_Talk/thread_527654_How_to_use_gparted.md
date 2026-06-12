---
title: "How to use gparted?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-16
I have the live cd, I'm just not sure how to actually USE it to partition, an explanation or link to a guide is much appreciated.

---

### Post by diatribe on 2007-08-16
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by MQMike on 2007-08-16
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by dljesse on 2007-08-17
I get an error every time I attempt to partition with gparted "check filesystem on /dev/sda1 for errors and (if possible) fix them." I don't mind formatting my hd that much, but I'd prefer not to. I'm sorry I can't make it anymore detailed, but thats exactly what the error message says.

---

### Post by mikewhatever on 2007-08-17
What is on dev/sda1 and what are you trying to do with it, resize (shrink/ expand), delete, what? It is asking you to run an integrity check. You can do it from Windows if you have it installed. You'll have to give more details, please.

---

### Post by dljesse on 2007-08-17
dev/sda1 is 180gb hd which currently only has feisty installed on it. The quote I provided in my previous post was the EXACT error message that I have received many times now. I'm trying to resize it and create a new partition so that I can re-install windows again. It doesn't say anything about an integrity check, if you don't have any clue I don't find reformatting my hd, but I'm not sure how to do that on feisty.

---

### Post by Ek0nomik on 2007-08-17
Relating to your error message:

[http://ubuntuforums.org/showthread.php?p=2357007](http://ubuntuforums.org/showthread.php?p=2357007)

[http://gparted-forum.surf4.info/viewtopic.php?pid=4257](http://gparted-forum.surf4.info/viewtopic.php?pid=4257)

[http://gparted-forum.surf4.info/viewtopic.php?pid=4287](http://gparted-forum.surf4.info/viewtopic.php?pid=4287)

From the suggestion in the first link:

```
chkdsk /f
```

This command is supposed to check the Windows partition for errors and fix them.  These links may help you on how to run chkdsk /f in Windows:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

[http://www.deltatranslator.com/chkdsk.htm](http://www.deltatranslator.com/chkdsk.htm)

---

### Post by mikewhatever on 2007-08-17
> **dljesse said:**
> dev/sda1 is 180gb hd which currently only has feisty installed on it. The quote I provided in my previous post was the EXACT error message that I have received many times now. I'm trying to resize it and create a new partition so that I can re-install windows again. It doesn't say anything about an integrity check, if you don't have any clue I don't find reformatting my hd, but I'm not sure how to do that on feisty.

It looks like no reformat is necessary at the moment. There is a utility in Ubuntu called fsck [http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm](http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm)
It should be able to check dev/sda1 for errors and fix them.
**Edit:** I've just checked it, and trying to run the check produced the following>  fsck /dev/sda5
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

That means it must be run from the live CD, when the partition in question in not mounted.

---

