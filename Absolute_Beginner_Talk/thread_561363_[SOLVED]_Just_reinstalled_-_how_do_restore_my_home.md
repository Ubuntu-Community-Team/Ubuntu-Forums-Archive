---
title: "[SOLVED] Just reinstalled - how do restore my home folder from my pen drive backup?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-27
Ok I couldnt work out the manual partition to give me a home partittion even after searching. So I did a guided using whole disk.
So now I got system back I need to restore my home folder without messing it up.
Preferable on a separate partition so I dont have to go through pain again.

---

### Post by zvacet on 2007-09-27
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by kyphi on 2007-09-27
Another way would be to back up your home folder onto an external hard drive.  I use a 60GB USB drive for that purpose but if your home folder is not very large, a pen drive would suffice.

Regular backups are a 'must do'.

---

### Post by philinux on 2007-09-28
> **kyphi said:**
> Another way would be to back up your home folder onto an external hard drive.  I use a 60GB USB drive for that purpose but if your home folder is not very large, a pen drive would suffice.

Regular backups are a 'must do'.

Cheers, If you read my thread title I have my backed up home folder on a pen drive what I want to do is restore it to a fresh install. Do I just copy it back and overwrite the installed home directory?
Having read the phsycocats it left me confused.

---

### Post by philinux on 2007-09-28
Ubump

---

### Post by kyphi on 2007-09-28
There is no need to duplicate your home directory folder.

When you insert your USB drive the contents will show up on the desktop.  Select all the items that you want to transfer, copy them, open your home directory and paste them.

or, if you find it easier...

open your home directory, move the screen over to the right, open your USB drive and move the screen over to the left, then select the contents of the USB drive and drag and drop them into your home directory.

There is no need to bump, half of the world is asleep while you are awake.

---

### Post by por100pre1 on 2007-09-28
> **philinux said:**
> Cheers, If you read my thread title I have my backed up home folder on a pen drive what I want to do is restore it to a fresh install. Do I just copy it back and overwrite the installed home directory?
Having read the phsycocats it left me confused.

I tried that before. I copied the files from my backed up /home/user folder, pasted them in my new /home/user folder and quickly did a CLI reboot. No problems.

---

### Post by philinux on 2007-09-30
Thanks to all my problem was that to backup the files initially I'd changed the ownership to root. Once I set it back to 700 it was fine.

---

