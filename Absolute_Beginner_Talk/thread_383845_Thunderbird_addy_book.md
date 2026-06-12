---
title: "Thunderbird addy book"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by holyowned on 2007-03-13
I am dual-booting XP/Ubuntu.  I have my Thunderbird mail on a FAT32 partition.
 Email folders and newsgroups are accessible in either OS, but Ubuntu is
not catching my address book.  Tips?
TIA

---

### Post by kolinab on 2007-03-14
Can you find a file called abook.mab?

On my system it's in /home/.mozilla-thunderbird/my profile directory.

I guess I should ask, where is the abook.mab file you access through windows stored? I don't know if it's possible to store it someplace other than your profile directory or not. I bet if it's someplace else on your windows system, and you move (hmm, back it up first) it into your profile directory you will be in business. 

Let us know how it goes.

---

### Post by holyowned on 2007-03-14
Yup, it is there.  The addy book for Windows is in FAT32/mozilla.default/.  I deleted the one in the Linux profile, and symlinked to the one on the FAT32.  When I launched TB, it said the address book was corrupt, backed it up, and created a new blank one.  I also opened both books in text editor, copy/pasted the FAT32 one into Linux.  Same result, corrupt addy book.

---

### Post by kolinab on 2007-03-14
I guess I'm confused. I was under the impression that your windows thunderbird and ubuntu thunderbird completely shared their data folders. So, I thought there would be just one file, shared by both OSs.

So I guess I'm over my head.

Maybe you should try the mozillazine forums? There's some good folks there:
[http://forums.mozillazine.org/index.php](http://forums.mozillazine.org/index.php)

---

### Post by holyowned on 2007-03-14
No, you are not confused.  When I installed TB in Ubuntu, I pointed it to the folder on my FAT32 partition.  I can download or compose email in either OS, reboot to the OTHER OS, and there is the mail I downloaded, or the message I saved, in the draft folder.  All my personal mail folders, filters........ except the addy book.

---

### Post by kolinab on 2007-03-14
Hmmm. What if you open the address book in Windows and *export* the address book. Then shut down T-bird, delete the old address book file, re-open T-bird and create a new address book. Then import your addy book from the exported file you just saved. 

I hope this makes sense - that kind of looks like one run on sentence. I guess that could eliminate the possibility that the address book really is corrupted. 

How does that sound, anyone?

---

### Post by holyowned on 2007-03-16
Export/import worked like a champ.  Thanks, Kolincab.

---

