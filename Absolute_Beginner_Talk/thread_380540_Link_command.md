---
title: "Link command?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-03-09
Hi all...I'm following through this "how to"...

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

and have reached the following paragraph (halfway down the HowTo, under the sub-heading "Changes in Edgy")

<snip HowTo>
This is the thorniest: the script won't correctly get rid of /var, and therefore can't link /var to /usr/var, which means GDM won't start and you'll be stuck in a shell. I have no idea why. In any case, I was able to fix it by booting into knoppix and deleting var off the unencrypted partition, then booting into single-user ("recovery") mode and linking it while the encrypted partition was correctly mounted. 
</snip>

I managed to delete /var using Knoppix, as the HowTo mentions.

For the linking instruction I used the command from the aforementioned script, namely....

ln -s /usr/var /var

However GDM still won't start and I'm stuck in a shell.

Simply put, my question is have I used the correct linking command as the HowTo doesn't explicitly give a command for this work-around. It seems to me I have but my ignorance is legend.

As an aside,  has anyone manged to complete this HowTo. The author says it's possible. I'm wondering how many others have succeeded.

Regards
Miguel

---

### Post by Miguellint on 2007-03-10
FWIW.....I manged to get it sorted by:

1) doing the aforementioned link command from the encrypted drive, then 

2) booting into Knoppix and mounting hda1 (with read/write permission) as /media/hda1, then 

3) hunting down the newly formed link (called var and found in /media/hda1/var) and temporarily moving it to the desktop, then 

4) deleting /media/hda1/var, then 

5) moving the link back to /media/hda1, then

6) successfully rebooting....

I've done things pretty much back to front but that's just the newbie in me. At least I understood what I was doing :-)

Huge respect to the author (Tobias?)

Regards
Miguel

---

