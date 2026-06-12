---
title: "Reset OS X password?"
date: 2006-09-03
forum: Apple PPC Users
---

### Post by koooldawg on 2006-09-03
I bought a second hand Power Mac G4 Quicksilver for $100 from a school district. Aparantly they put OS X server on it. They wont give me the password and they cant find the install disc. ](*,)  I just got Ubuntu for PPC in the mail. I want to know if I can use Ubuntu Live CD to change/reset the password on OS X and how? :confused: 

I've had some expiriance with many Ubuntu and other distros of linux, but only on intel. :-D I have like no idea what im doing in Mac and I dont know many terminal commands in linux.

Please Help! :cry:

---

### Post by calum on 2006-09-04
> **koooldawg said:**
> I bought a second hand Power Mac G4 Quicksilver for $100 from a school district. Aparantly they put OS X server on it. They wont give me the password and they cant find the install disc. ](*,)  I just got Ubuntu for PPC in the mail. I want to know if I can use Ubuntu Live CD to change/reset the password on OS X and how? :confused: 

I've had some expiriance with many Ubuntu and other distros of linux, but only on intel. :-D I have like no idea what im doing in Mac and I dont know many terminal commands in linux.

Please Help! :cry:

Which password, user login or firmware?    If it's the firmware password, opening up the Mac and temporarily removing some RAM will reset it.  Even then, you'll still have the problem of logging in, if you don't know any of the user or admin account passwords, though. 

Check out [http://docs.info.apple.com/article.html?artnum=106482](http://docs.info.apple.com/article.html?artnum=106482) and [http://docs.info.apple.com/article.html?artnum=106156](http://docs.info.apple.com/article.html?artnum=106156) for some relevant info as well.

Main lesson: don't buy computers without install discs, you never know when you'll need them :/  I guess, since you bought the machine legitimately, Apple *might* supply you with a replacement install disc, if the previous owners registered their software and explain to Apple that it's been lost.

---

### Post by koooldawg on 2006-09-04
> **calum said:**
> Which password, user login or firmware?    If it's the firmware password, opening up the Mac and temporarily removing some RAM will reset it.  Even then, you'll still have the problem of logging in, if you don't know any of the user or admin account passwords, though. 

Check out [http://docs.info.apple.com/article.html?artnum=106482](http://docs.info.apple.com/article.html?artnum=106482) and [http://docs.info.apple.com/article.html?artnum=106156](http://docs.info.apple.com/article.html?artnum=106156) for some relevant info as well.

Main lesson: don't buy computers without install discs, you never know when you'll need them :/  I guess, since you bought the machine legitimately, Apple *might* supply you with a replacement install disc, if the previous owners registered their software and explain to Apple that it's been lost.

there was no firmware password set. and the other article requires a disc. ](*,) 
i know theres got to be another way, cause some guy around here wants me to pay him $55 to do it and he knows everything ive tried. Im broke, so i cant pay him. someone suggested using BSD to do it, but isnt linux and BSD the same?

---

### Post by calum on 2006-09-05
> **koooldawg said:**
> there was no firmware password set. and the other article requires a disc. ](*,) 
i know theres got to be another way, cause some guy around here wants me to pay him $55 to do it and he knows everything ive tried. Im broke, so i cant pay him. someone suggested using BSD to do it, but isnt linux and BSD the same?

BSD is a flavour of Unix, and essentially the same as the one on which OSX is based so I guess that's why it was suggested.  Linux and Unix aren't quite the same thing, but they're similar enough that I'm not sure you'd need to use BSD for this task.

I expect it's possible to mount the OSX partition in Linux/Unix and manipulate the files on that partition directly to create a new user account that you could use to log in.   Unfortunately I don't have enough working knowledge of the OSX files you'd need to modify to do this... if you don't get any help here, you might have better luck checking or asking on [Apple's discussion forums]("http://discussions.apple.com"), or check out a book like [OSX For Unix Geeks](http://www.oreilly.com/catalog/macxtigerunix/).

---

### Post by jdp on 2006-09-07
The guy that wants the money to do it pobably has access to some install discs.  You don't need the actual discs that it was installed with, just ones of the same version.  If you know someone who runs/works at a place where they use OS X Server, ask if you could bring the machine by to get the passwork reset.  Heck, ask at an Apple repair shop or an Apple Store, too.  But really, unless you plan on using OS X Server, you might as well get a copy of Tiger and reformat and reinstall anyway.

Or, just wipe and install olny Ubuntu. ;)

---

### Post by 3rdalbum on 2006-09-08
By reading this month's Linux Format, I think there might be a way for you to do it with Linux, assuming Mac OS X Server is enough like Linux. Be aware that I've never tried this, or anything similar, before; and all I know about this subject is what I've read in a magazine and what I'm guessing from this limited knowledge.

Please don't hold me responsible if these instructions don't work or if they make it impossible to salvage the OS X install.

Boot up using the Ubuntu Live CD. You now must mount the computer's hard disk - I'm useless at manually mounting stuff, so it would probably be a good idea to look online or in this forum for how to mount OS X disks.

Once it's mounted, open up the files /etc/passwd and /etc/shadow in a text editor. You will notice that /etc/passwd has all the user account details, and /etc/shadow has encrypted (or rather, hashed) passwords for those user accounts.

On another Linux system where you know the root password, open up the /etc/shadow file. Find the entry which corresponds to the **root** account (it should be much longer than the others, and probably start with $1$), and replace the password field for **root** in /etc/shadow on the OS X box, with the one in the /etc/shadow file on the Linux box.

This will, hopefully, change the password on the OS X computer to be the same as the one on the Linux computer. Save the file and restart the computer. Be aware that I don't really know what I'm talking about, I'm just inferring stuff from what I've read in a magazine. Please only try these instructions as a last resort, when you decide you don't mind if you lose the OS X server.

---

### Post by stmiller on 2006-09-08
You should be able to change the password with the OS X install disc. Though you might need the OS X Server disc, in your case.

---

