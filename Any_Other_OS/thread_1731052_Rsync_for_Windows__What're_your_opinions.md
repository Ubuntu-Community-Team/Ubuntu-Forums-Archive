---
title: "Rsync for Windows?  What're your opinions?"
date: 2011-04-16
forum: Any Other OS
---

### Post by akakingess on 2011-04-16
Okay,

I know this is the Ubuntu forums and not great protocol, but I value the opinions on this forum above all else, so could anyone recommend an equivalent to rsync/grsync for the Windows 7 OS? I have to use Windows for work, but want to do my own backing up and love grsync and would like something as close to it as possible, so what are your thoughts/opinions. As always, all ideas are welcome and thanks in advance for your time and consideration.

---

### Post by uRock on 2011-04-16
Moved to Other OS/Distro Talk

---

### Post by Keypel on 2011-04-16
I stay as far away from windows as possible but I used to use a Microsoft program called Handy Backup. It's paid software with one of those 30-day free trial things. That's another reason to like Linux, all the software I have ever seen has been free.

---

### Post by akakingess on 2011-04-17
> **Keypel said:**
> I stay as far away from windows as possible but I used to use a Microsoft program called Handy Backup. It's paid software with one of those 30-day free trial things. That's another reason to like Linux, all the software I have ever seen has been free.


Trust me I am with you as far as staying as far away from Windows as possible, but since I have to use it for work, I want a reliable backup program just because of the notorious Windows ;)

---

### Post by mips on 2011-04-17
[http://www.techsupportalert.com/best-free-backup-program](http://www.techsupportalert.com/best-free-backup-program)
[http://www.techsupportalert.com/best-free-folder-synchronization-utility.htm](http://www.techsupportalert.com/best-free-folder-synchronization-utility.htm)

[http://en.wikipedia.org/wiki/Rsync#GUIs](http://en.wikipedia.org/wiki/Rsync#GUIs)

No idea about rsync on widows but the above links might be useful. grsync runs on windows so why not try it out. There are also other gui's as per the wikipedia link.

---

### Post by SeijiSensei on 2011-04-17
How about xcopy?

---

### Post by walt.smith1960 on 2011-04-21
I used this with Windows.  [http://www.2brightsparks.com/syncback/](http://www.2brightsparks.com/syncback/)   I used the freeware version; it was adequate for my purposes.

---

### Post by CharlesA on 2011-04-21
I've been using robocopy to sync (or mirror) directories on Windows.

It's kinda like rsync, but not quite.

---

### Post by collisionystm on 2011-04-21
> **akakingess said:**
> Okay,

I know this is the Ubuntu forums and not great protocol, but I value the opinions on this forum above all else, so could anyone recommend an equivalent to rsync/grsync for the Windows 7 OS? I have to use Windows for work, but want to do my own backing up and love grsync and would like something as close to it as possible, so what are your thoughts/opinions. As always, all ideas are welcome and thanks in advance for your time and consideration.

2 ways to do it.

Use robocopy and build a .batch script to run it, put it on an automatic schedule to run everynight.

OR

Share the root of your C: drive on windows, set the permissions so only the administrator can access the share.

Mount the drive on linux using smbmount

Now that the drive is mounted on linux, 

Use rsync to backup that mounted drive to another folder on the linux box.

Dont waste your time searching for rsync programs for windows. I spent a few days finding one that works good.

nearest thing I could find that was worth using is called bonky " bonky the backup monkey"

---

### Post by teejay17 on 2011-04-22
> **akakingess said:**
> Okay,

I know this is the Ubuntu forums and not great protocol, but I value the opinions on this forum above all else, so could anyone recommend an equivalent to rsync/grsync for the Windows 7 OS? I have to use Windows for work, but want to do my own backing up and love grsync and would like something as close to it as possible, so what are your thoughts/opinions. As always, all ideas are welcome and thanks in advance for your time and consideration.
I used GRsync on Windows. It wasn't bad and has the same look as on Ubuntu, if you are concerned about consistency across all platforms. There is also one called Unison that i haven't tried yet, but have researched and seems to have excellent reviews online. It appears that it is more robust and feature rich, as well as being cross platform. [http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)

---

### Post by walt.smith1960 on 2011-04-23
> **teejay17 said:**
> I used GRsync on Windows. It wasn't bad and has the same look as on Ubuntu, if you are concerned about consistency across all platforms. There is also one called Unison that i haven't tried yet, but have researched and seems to have excellent reviews online. It appears that it is more robust and feature rich, as well as being cross platform. [http://www.cis.upenn.edu/~bcpierce/unison/index.html]("http://www.cis.upenn.edu/%7Ebcpierce/unison/index.html")

Unison in in the universe repositories. I downloaded it but don't have anything to synchronize right now.  It appears pretty straightforward to use. Segueing into a Unity criticism, Unison shows up if I search for it but doesn't show up when I select "show all apps"

---

