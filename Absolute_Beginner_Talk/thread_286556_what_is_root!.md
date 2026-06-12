---
title: "what is root!??"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-27
i just want to know what is root?when u are running as root admin or something and what priorities does that give you and how you do it!?
10x

---

### Post by tonyr1988 on 2006-10-27
root basically lets you do anything and everything that you could possibly want to your computer. In Windows, this is called "Administrator".

The problem? It also means all your *programs* can do things to your computer.

Instead, Ubuntu doesn't allow you to run as root. This way, "bad" programs can't do "bad" things to your computer. We have what's called "sudo". This is, in effect, temporary root. If a program wants to run and do things to your computer that could mess it up, you have to type in your password to verify that it's something you want to allow it to do.

Make sense?

---

### Post by Dual Cortex on 2006-10-27
When you log in as 'root,' you pretty much have total control of every file/setting on your computer. This is why using root as a main account around while in root mode isn't recommended.
Your normal account is pretty much also and administrator account except every time you always want to perform an administrator-esque action you need to provide your password.

For example you can't just edit your sources.list file and save it by just browsing to its location, opening it, etc., on your normal user acct. If you are in a root account, you can just browse to it and edit it as if it were a love letter.

---

### Post by Sam on 2006-10-27
[Root ?](http://en.wikipedia.org/wiki/Superuser)
[How Ubuntu handle root](https://wiki.ubuntu.com/RootSudo)

---

### Post by fatsheep on 2006-10-27
The account you log into is a limited account to prevent accidental damage to your system.  On the other hand, the root account is **unlimited**.  It can do anything and everything which is why you should be careful when you use root - you could damage your system.  

If you want to run a command in the terminal as root simply prefix it with "sudo" or "gksudo" for graphical applications.  So, if you want to use nautilus (the file browser) as root then you would type "gksudo nautilus".  If you like using nautilus as root then you could make a script on your desktop to start it automatically.  Just make an empty text file (without an extension).  Paste this into it using text editor:

> 
#!/bin/bash
gksudo nautilus


Save.  Now right click on the file, go to properties and then to permissions.  Make sure you (the owner) have permission to execute it.  Now double click on it and either click "Run" or "Run In Terminal".  I think either one should work.  

On a side note, if you would like it to start up in a different directory then the default then just add the path to your preferred location after "nautilus".  For example, if I wanted nautilus to start in the directory /etc I would use this for my shortcut:

> 
#!/bin/bash
gksudo nautilus /etc


Hope this helps,

-sheep

---

### Post by ReaderRat on 2006-10-27
[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

