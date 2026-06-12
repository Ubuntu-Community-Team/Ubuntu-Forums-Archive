---
title: "security of files"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by strnad on 2008-02-05
Hello,

I am using Ubuntu also due to the security. However I have read, that despite I encrypt the file, in cache, unencrypted files can be found.

This however totally undermines the security of my files (mainly odf).

How can I solve this problem? Is a solution to create a virtual encrypted disc (with. TrueCrypt e.g.) and save all my files there? Or safely erase cache with some erasing program? Where however can I find these cached files?

Thanks 

Peter

---

### Post by Joeb454 on 2008-02-05
Why do you need to secure your files so much? Just so we know...I mean, I'm sure the cache gets emptied on reboot.

If you're concerned about the security of your files store them on a portable drive which is totally encrypted or something

---

### Post by hyper_ch on 2008-02-05
> **Joeb454 said:**
> Why do you need to secure your files so much? Just so we know...I mean, I'm sure the cache gets emptied on reboot.
But it can still be recovered.. also the nature of journaling filesystem makes it harder to encrypt specific files with all their copies....

The simplest solution would be a full system encryption. That will however slowdown big read/writes on your system - but everyting would be encrypted and you wouldn't have to worry about each copy.

---

### Post by Joeb454 on 2008-02-05
I guess thats one option. Though not viable for me (lots of big read/writes over a network).

Also just to make sure, would the portable drive option I suggested work? I've never tried myself

---

### Post by hyper_ch on 2008-02-05
> **Joeb454 said:**
> Also just to make sure, would the portable drive option I suggested work? I've never tried myself
There would still be the swap that would be required to encrypt also.

---

### Post by solitaire on 2008-02-05
I'm not 100% sure...

But some of the encryption programs usualy only use systam RAM to decrypt encrypted files so there should be no cached copy of the decrypted file on the disk. (I know that Windows version of PGP Could be set to use RAM to view encrypted files) The same option should be availble for all other encryption programs. Also a good wipe program should remove any traces of deleted files..

---

### Post by lex1 on 2008-02-05
best  bet to encrypt root  home and swap is loop-aes

lex1

as i understand it the lateast sid installer at debian.org would do it
from the installer menu but the sysyem installed is lenny
but thats another debian disto and another story

---

### Post by hyper_ch on 2008-02-05
the alternate install cd does it also since gutsy.

---

