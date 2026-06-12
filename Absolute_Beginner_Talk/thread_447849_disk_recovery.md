---
title: "disk recovery"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-05-18
i recently had a bad error and hed to reinstall ubuntu. but that's in the past. what i want to know is if there is any good file recovery software that i can get?

---

### Post by hyper_ch on 2007-05-18
I don't trust file recovery software... you're better of making backups automatically at a given interval...

---

### Post by rickycodie on 2007-05-18
thanks i've already started doing that but i still need some old files, any good programs out there?

---

### Post by brennydoogles on 2007-05-18
> **rickycodie said:**
> i recently had a bad error and hed to reinstall ubuntu. but that's in the past. what i want to know is if there is any good file recovery software that i can get?

There is a wonderful piece of software (available in Synaptic) call TestDisk. It will check disks for all kinds of failures, and it also comes with PhotoRec, which will recover files from past installations. PhotoRec wiki can be found [here]("http://www.cgsecurity.org/wiki/PhotoRec"). You should note that any files it saves will be renamed to random letters and numbers, and will be split up into tons and tons of random folders. You can consolidate the files for easier browsing by following [this thread]("http://ubuntuforums.org/showthread.php?t=442749"), and it will also tell you how to organize them by filetype from there. I don't know how it will do if you are running it on the disk you have Ubuntu installed on, and you may have all kinds of crap left over that you don't want, but it is often better than losing data. If you need any help let me know!!!

---

### Post by chamberlain2006 on 2007-05-18
A good practice is to keep your /home directory on a separate partition, so that even when you reinstall, you data won't be removed.  A good howto is [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by rickycodie on 2007-05-18
thanks to all but especially brennydoogles. i will try all suggestions.

---

### Post by brennydoogles on 2007-05-18
no problem, check your PM's I sent you something that will help if you use PhotoRec

---

### Post by Sef on 2007-05-19
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

> no problem, check your PM's I sent you something that will help if you use PhotoRec

Please post help for that in the forums, so everyone can benefit.  Thank you.

---

### Post by brennydoogles on 2007-05-19
> **Sef said:**
> Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").



Please post help for that in the forums, so everyone can benefit.  Thank you.

No problem, but I do need to post the same disclaimer that I posted before.The help that I gave in the PM was a script I wrote to take all of the files from the several hundred directories that PhotoRec could possibly make, and  split them up by type for easier digging. I wrote this script from my windows machine (because my linux box is fried right now) so I have not had a chance to test it to make sure it works. It is also my first script (full of commands that I have used alot lately), so it may have a few things I need to update to make it run smoothly. I will gladly attach it, and anyone can feel free to suggest updates (such as syntax updates or more file extensions for each type of file). I hope it helps a few people!

---

### Post by rickycodie on 2007-05-19
maybe we can sticky this?

---

