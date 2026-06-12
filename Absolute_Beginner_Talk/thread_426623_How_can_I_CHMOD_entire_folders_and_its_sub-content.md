---
title: "How can I CHMOD entire folders and its sub-contents?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-04-28
How can I CHMOD entire folders and its sub-contents?
Azureus is having trouble installing plugins because it ain't root. Previously I had to CHMOD each and every file and folder.  Now I want to CHMOD things smarter.

Howto?

---

### Post by sessine on 2007-04-28
doing

```
chmod -R <options> <directoryname>
```

will make chmod descend into directories

---

### Post by Malibu Illusion on 2007-04-28
Use flag -R:

chmod -R [permissions] [dir name]

---

### Post by jingo811 on 2007-04-28
tnx!
By the way is it secure to CHMOD 777 entire /opt folder?
Or should I only do that for each selected program folder such as Azureus, XAMPP, etc. etc.?

---

### Post by Metacarpal on 2007-04-28
Personally, I wouldn't chmod 777 anything only one level down from root.  Just 777 the Azureus folder - or better yet, if the Azureus process runs under your username only (ie, you're the only user to run it), chown the Azureus folder and chmod 755.

---

### Post by Tomosaur on 2007-04-28
You shouldn't change the permissions of anything outside your home directory, because you will almost certainly break your system. Easiest way to allow azureus to sort itself out is to run it as root, configure everything, then exit and run it as an ordinary user.

---

### Post by jingo811 on 2007-04-29
roger.

---

### Post by Najand on 2007-04-29
/opt folder is the place, some commercial softwares install their files there. Why do you need to chmod 777 /opt?

---

### Post by jingo811 on 2007-04-29
> You shouldn't change the permissions of anything outside your home directory, because you will almost certainly break your system. Easiest way to allow azureus to sort itself out is to run it as root, configure everything, then exit and run it as an ordinary user.
On the other hand I'll take back that roger.  It's too annoying I have to "gksudo azureus" everytime there needs to be update, remove and so forth.  I'm gonna risk it by going 777, Windows was much better at handling the Azureus experience.


> /opt folder is the place, some commercial softwares install their files there. Why do you need to chmod 777 /opt?
Becauce Azureus installs its folder in there.  And also I'm experimenting with Apache+PHP (XAMPP) which also installs in that folder.  I can't save my workfiles in /opt sub folders, and update and plugin removal on Azureus is a pain.

It's smoothest to CHMOD them 777 so that things just happen how you want them to happen.

---

### Post by Tomosaur on 2007-04-29
> **jingo811 said:**
> On the other hand I'll take back that roger.  It's too annoying I have to "gksudo azureus" everytime there needs to be update, remove and so forth.  I'm gonna risk it by going 777, Windows was much better at handling the Azureus experience.

My suggestion was only that - a suggestion. I have no personal experience with azureus. The very fact (if it IS a fact) that you would even need to use sudo just to configure it seems to me to indicate that it's a badly written piece of software. You may be much better off trying to find an alternative which was written with some sanity.

The choice is ultimately up to you, however, it's your machine. You may find it is more annoying, however - when you realise the massive mistake you will be making by chmodding outside of your home dir, and find that other things break, all because you didn't want to put up with entering a password every couple of weeks / months.

---

### Post by Compyx on 2007-04-29
> **jingo811 said:**
> On the other hand I'll take back that roger.  It's too annoying I have to "gksudo azureus" everytime there needs to be update, remove and so forth.  I'm gonna risk it by going 777, Windows was much better at handling the Azureus experience.


In Windows you run with full rights by default, which may seem convenient, but is also one of the main causes of the spread of malware, viruses and worms. What's so horrible about having to enter a password now and then? Recursively chmod'ing /opt to 777 is asking for trouble in my book.

---

### Post by jingo811 on 2007-04-30
> The choice is ultimately up to you, however, it's your machine. You may find it is more annoying, however - when you realise the massive mistake you will be making by chmodding outside of your home dir, and find that other things break, all because you didn't want to put up with entering a password every couple of weeks / months.
OK then I chmod it 777 the first week or so for updates and repairs, then I switch it back to 755 again. :)

---

