---
title: "[SOLVED] Teaching Ark 7zip, rar, ace"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-08-24
Hello,

How can I teach Ark new/extra archive formats?

Cheers,
Sidd

---

### Post by LaRoza on 2007-08-24
> **siddartha said:**
> Hello,

How can I teach Ark new/extra archive formats?

Cheers,
Sidd

What do you mean "Teach"?

If you want a good archive tool, try 7-Zip.

---

### Post by dulbirakan on 2007-08-24
It is all too easy, just use open "Add/Remove Applications" as you would do for installing any other program and select the following programs:

7zip (it is on top of the list, see?)
ACE
RAR

If you cannot see these programs in the list then make sure that "All available applications" is selected in the show menu (which is just right to the search box it might be showing "Supported Ubuntu Applications").

Hope that will help...

---

### Post by siddartha on 2007-08-24
I mean like being able to tune up the options. Make 7zip archive means almost nothing as there are so many things to set up like dictionary size, compression even different compression algoritms.

---

### Post by siddartha on 2007-10-16
7zip for windows in a wine environment, that should be the answer so far.

---

### Post by stchman on 2007-10-16
> **siddartha said:**
> Hello,

How can I teach Ark new/extra archive formats?

Cheers,
Sidd

You need to install the appropriate plugin packages.

rar - install rar and unrar
7zip - install p7zip p7zip-full

```
sudo apt-get install rar unrar p7zip p7zip-full
```

After installation of these packages you will be able to pack/unpack these archives.

File Roller and Ark can already deal with the popular ones like .gz, tar.gz, .zip, tar.bz2, etc.

---

### Post by siddartha on 2007-10-16
Read the thread for an explanation.

---

### Post by adredwood on 2007-10-17
Hey - nothing new to add, just thought id support what&#347; been said here - i was having problems opening some multi-part rars, and couldnt figure otu why the archiver didnt want to know about them at all. Then hey presto - install Ace and RAR from add/remove programs, works like a smooth silky thing.

Thankyou, knowledgeable ones...

Andy (:

---

