---
title: "Unable to change permisions on file sysytem &quot;im not the owner&quot;... I AM!"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-10-26
I wanted to change my splash screen and i need to copy something to my  file system, it wont let me and when i try to change the permissions on it, it says im not the owner!...help plz](*,)

---

### Post by jorn on 2006-10-26
Edit: Sorry, I didn't read your post properly.

---

### Post by robenroute on 2006-10-26
***[COLOR="DarkRed"]Forget it?[/COLOR]***

---

### Post by PriceChild on 2006-10-26
Precede the command you are using with "sudo". This will give the command root privelages and the ability to do anything.

Read more at [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

> **jorn said:**
> Forget it.Please ignore him.

---

### Post by jorn on 2006-10-26
[QUOTE]Forget it? [QUOTE]
Sory for that. I as posting something without having read the post correct.
Then I just wantet to let you forget what I posted. It was not ment on your question. I apologize.

---

### Post by happy-and-lost on 2006-10-26
In terminal type "sudo nautilus" to open the Nautilus file manager as root if you want to work from Nautilus itsself (which you probably do!)

---

### Post by jefuchs on 2006-10-26
I'm new to Ubunto too, but here's how I did it.  I copied the file using the command line.  Before the command I typed *sudo*, which tells the system I am the administrator (and that I own the files).  Then it prompted me for a password, and it proceeded to copy the file.

Here's my command exactly..

sudo cp /home/jeff/Desktop/flash/libflashplayer.so ~/.mozilla/plugins 

One thing that made this very difficult was that I forgot that in Linux "Desktop" is not the same as "desktop".  In Windows you don't have to match case.

---

