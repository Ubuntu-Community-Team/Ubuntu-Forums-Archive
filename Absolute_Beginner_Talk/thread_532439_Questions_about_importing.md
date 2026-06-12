---
title: "Questions about importing"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-08-22
Before I install Ubuntu to duel boot with Windows XP, I want to be sure of a few more things.
I understand that the installer gives you an option to import data from XP, but I have a few questions about that. (all data is on the same HDD)
1. Will the files I select for import still be available in XP? 
2. Since this is a family computer, there are multiple XP accounts. Can I select which account files are being imported from? (example: My Documents from User A, but not from User B or C). 
3. When files are imported, will they convert to files usable in Ubuntu? (mp3 to ogg, ect.) If so, can I stop this? I know Ubuntu can't natively read files like wma, mp3, or wmv, but I need to keep them in this formate so I can sync them to my mp3 player.
-Thanks!

---

### Post by qamelian on 2007-08-22
> **Aiello said:**
> Before I install Ubuntu to duel boot with Windows XP, I want to be sure of a few more things.
I understand that the installer gives you an option to import data from XP, but I have a few questions about that. (all data is on the same HDD)
1. Will the files I select for import still be available in XP? 
2. Since this is a family computer, there are multiple XP accounts. Can I select which account files are being imported from? (example: My Documents from User A, but not from User B or C). 
3. When files are imported, will they convert to files usable in Ubuntu? (mp3 to ogg, ect.) If so, can I stop this? I know Ubuntu can't natively read files like wma, mp3, or wmv, but I need to keep them in this formate so I can sync them to my mp3 player.
-Thanks!

1) Yes
2) Yes
3) No conversion takes place. Files are migrated as is.

---

### Post by expatCM on 2007-08-22
Data files are imported from XP?

I have set up Ubuntu many times now and on the dual boot machines I had never realized that Data was imported.  I know that accounts settings may be imported but I had never thought that Data was affected.

So what happens?  Is the content of a users My Documents folder copied over to the user /Home directory or what?

---

### Post by qamelian on 2007-08-22
> **expatCM said:**
> Data files are imported from XP?

I have set up Ubuntu many times now and on the dual boot machines I had never realized that Data was imported.  I know that accounts settings may be imported but I had never thought that Data was affected.

So what happens?  Is the content of a users My Documents folder copied over to the user /Home directory or what?

The migration tool is part of the installer found on the desktop CD starting with Feisty. It attempts to move files from My Documents in Windows to your $Home folder in your new Linux install. It also tries to migrate other stuff as well, such as browser bookmarks and email account settings, I believe. Can't remember for sure as I've only used it once on a test box.

---

### Post by avik on 2007-08-22
> **Aiello said:**
> 
3. When files are imported, will they convert to files usable in Ubuntu? (mp3 to ogg, ect.) If so, can I stop this? I know Ubuntu can't natively read files like wma, mp3, or wmv, but I need to keep them in this formate so I can sync them to my mp3 player.

As qamelian said, no files are converted.  However, Ubuntu can still view most Windows-compatible files (.mp3, .doc, etc.) by installing codecs or using the right programs (OpenOffice.org for example can read and edit .doc files just fine).

---

