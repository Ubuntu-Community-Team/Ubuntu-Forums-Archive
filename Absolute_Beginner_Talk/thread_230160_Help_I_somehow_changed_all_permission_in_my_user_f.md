---
title: "Help: I somehow changed all permission in my user folder, therefore cannot log in"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2006-08-05
I have a problem and I think it is because it changed permissions to every single files in my usr home folder.

huguette@browserice-desktop:/home$ ll
total 16
drwxr-xr-x  4 root       root       4096 2006-07-27 01:57 .
drwxr-xr-x 21 root       root       4096 2006-07-27 01:23 ..
drw-rw-rw- 24 browserice browserice 4096 2006-08-05 13:08 browserice
drwxr-xr-x 12 huguette   huguette   4096 2006-08-05 13:50 huguette

I had just copied my MP3 files from my DVD and noticed that I had permission problems when trying to remove some files off of the newly created MP3 folder. So while using the File Browser, I went into that MP3 local folder, did a select-all, and changed the permission to rw- . I then had a bunch of popups telling me I couldn't change the permission but then, the whole system froze. So I rebooted but when I wanted to log back, it said something about not having permission to write to my .../.gnome2/ folder. Prior to that, right after logging in, it told me some file was being skipped and therfore, my setings (language, ...) wouldn't be saved.

I need that logon back. It is my admin logon. The current user I am using to write this post is for my wife and I don't think it has all the necessary access to fix this !


I need this bad !

---

### Post by user1397 on 2006-08-05
> **Browser_ice said:**
> I have a problem and I think it is because it changed permissions to every single files in my usr home folder.

huguette@browserice-desktop:/home$ ll
total 16
drwxr-xr-x  4 root       root       4096 2006-07-27 01:57 .
drwxr-xr-x 21 root       root       4096 2006-07-27 01:23 ..
drw-rw-rw- 24 browserice browserice 4096 2006-08-05 13:08 browserice
drwxr-xr-x 12 huguette   huguette   4096 2006-08-05 13:50 huguette

I had just copied my MP3 files from my DVD and noticed that I had permission problems when trying to remove some files off of the newly created MP3 folder. So while using the File Browser, I went into that MP3 local folder, did a select-all, and changed the permission to rw- . I then had a bunch of popups telling me I couldn't change the permission but then, the whole system froze. So I rebooted but when I wanted to log back, it said something about not having permission to write to my .../.gnome2/ folder. Prior to that, right after logging in, it told me some file was being skipped and therfore, my setings (language, ...) wouldn't be saved.

I need that logon back. It is my admin logon. The current user I am using to write this post is for my wife and I don't think it has all the necessary access to fix this !


I need this bad !okay i had the same problem and this is what i was told to do, and it worked.  login to the failsafe terminal, and type: ```
chmod -R ugo+X /home/huguette
```and then login to your regular session.  it should work!

---

### Post by Browser_ice on 2006-08-05
It was my browserice id that was affected by this.

I am talking in the past because I couldn't wait and did a partition restore with my True Image 9 image DVD backup. I am using that id right now.

That image is dated of 2 weeks max and I didn't installed much new stuffs since then so it seamed like a good and quick solution.

Still, can you explain the command and options you gave me ?

---

### Post by Browser_ice on 2006-08-05
Never mind explaining it. I found out through [Google]("http://www.comentum.com/unix-osx-permissions.html")


[INDENT] chmod -R ugo+rwx directoryname
"-R" - means recursively change permissions of directories and their contents.[/INDENT]

In other words, they told you to change the permission to every single files in every single folders. It maybe a workaround but I don't think it is a safe workaround.

Having a mean to **restore** permissions to what they were before is more safe way. But then again, I don't think it is possible without having somekind of backup.

Speaking of backups, maybe I should install an incremental Cron backup ...

---

### Post by user1397 on 2006-08-05
> **Browser_ice said:**
> It was my browserice id that was affected by this.

I am talking in the past because I couldn't wait and did a partition restore with my True Image 9 image DVD backup. I am using that id right now.

That image is dated of 2 weeks max and I didn't installed much new stuffs since then so it seamed like a good and quick solution.

Still, can you explain the command and options you gave me ?well basically, i was making your username's home folder recursively executable.  That means that every file and folder would become executable in /home/huguette.  The thing is, when I did that command, it actually restored the default permissions to many important files in /home/erik, so that it worked as flawlessly as before.

---

