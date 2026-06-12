---
title: "Encryption"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2008-03-01
hey,

would you guys reccomend TrueCrypt?

(Ive never used it before- just wanna encrypt external HD for offsite backups)


thanks in advance!!

---

### Post by gobbles414 on 2008-03-01
JasonBourneLinux,

I really like [CryptKeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html"). It's a lot easier to use than TrueCrypt, IMHO. However, as far as I know there isn't a Windows or OS X version of CryptKeeper. So, TrueCrypt would be a better choice if you need your encrypted backups to be accessible in multiple operating systems. A Windows-only encryption program that I like is called [My Lockbox]("http://www.fspro.net/folder-lock-box/"). Does that help?

---

### Post by JasonBourneLinux on 2008-03-01
thanks for the help

---

### Post by gobbles414 on 2008-03-01
> **JasonBourneLinux said:**
> thanks for the help

My Pleasure! Which program have you decided to use?

---

### Post by JasonBourneLinux on 2008-03-01
I'll probably use TrueCrypt because I need multi platform support (and others have recommended it to me as well)

---

### Post by wieman01 on 2008-03-01
+1 for Truecrypt. It is the most reliable (and portable) encryption software that I know of... at least in the OS resort. Let us know if you need a hand, but it is fairly simple to use.

---

### Post by JasonBourneLinux on 2008-03-01
thanks!!

First question- should I make one of the encrypted bins and transfer it to my external or simply encrypt my whole external? (lol which one is easier?)

---

### Post by wieman01 on 2008-03-01
WIth the new GUI, both procedure are fairly simple. I would go for a whole-disk encryption. This way nobody would be even able to make a copy of your files/container (at least average users would not be able to do it).

The default file system format is FAT. If you need NTFS or EXT3, you need to do a bit of terminal work, but it's possible. Let me know...

---

### Post by JasonBourneLinux on 2008-03-01
ahhh but TrueCrypt can work with NTFS as well? (I might work with TrueCrypt's GUI in windows)

Could you show me how to do it?

thanks in advance!

---

### Post by wieman01 on 2008-03-01
Yes, it can. You either format it using Windows, or you take a look at this post:

This is how you would make an 'ext3' files system, but I am not sure if Ubuntu can format to NTFS...
> 1. Use the GUI and create a FAT filesystem.
2. Mount the new Truecrypt volume using the GUI
3. Open a terminal and type mount
4. Unmount the truecrypt volume. For me it was umount /media/truecrypt1
5. Create the new file system. For ext3 use the following:
sudo mkfs -t ext3 /dev/loop0
6. Remount the drive using the GUI if you want.
This is a quote from [here]("http://ubuntuforums.org/showthread.php?t=689165&page=9").

If Linux cannot do it, then use Windows to create the volume. I am not sure how good Ubuntu is these days at writing to an NTFS volume. Reading from it should be OK, but writing used to be an issue.

---

### Post by JasonBourneLinux on 2008-03-01
think it should be ok- NTFS-3g has been integrated into 7.10 right?

---

### Post by wieman01 on 2008-03-01
Yes, that is true. Give it a try. Just format it using Windows and you should be fine...

---

