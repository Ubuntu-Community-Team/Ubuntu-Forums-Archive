---
title: "mount network drive"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by freshspinach on 2007-09-16
how do i permanently mount a network drive so that i can, for example, add my entire music collection to exaile? i can't see my network drive in exaile but i can access it through nautilus without a problem.

i'm running feisty with samba. my network drive is ntfs on a feisty server using samba.

---

### Post by Nikitas350 on 2007-09-16
Try this: Go to Places-----> COnnect to server
and add the preferences you want. This will make a link to your desktop to the server.... :)

---

### Post by freshspinach on 2007-09-16
I tried that but was only able to connect using the 'custom location' way. It didn't change my inability to access my network drive from Exaile.

---

### Post by freshspinach on 2007-10-14
bump

---

### Post by dmartin on 2008-01-29
I know this is a bit old, but since it is unanswered...

I use sshfs.  You have to install it.
> sudo apt-get install sshfs" 

You need to add yourself to the fuse group.

Then you mount it using something like:
> sshfs myusername@myremotemachine:/home/myhome "/home/myhome/somefolder"

The local folder must exist.  Also, you will be prompted for your password.  Ideally, you put this in your .profile so it gets mounted automatically.  But first, you'd need to eliminate the password.  To do this, follow these instructions to make your client machine trusted, but in a secure way:  [http://www.oreilly.com/pub/h/66](http://www.oreilly.com/pub/h/66)

Once you do that, you should be able to add your sshfs command to the bottom of .profile, and you'd get the folder mounted at login.  

If you prefer, you can add it to /etc/fstab so it will get mounted at boot up.  The problem I have with that is that I suspect it is less secure because it is mounted without a login, and getting it mounted where you have ownership takes some tricky configuration.

The great thing about sshfs is that programs cannot tell the difference between this and a local filesystem.  I've yet to find a program that didn't work with sshfs.

---

