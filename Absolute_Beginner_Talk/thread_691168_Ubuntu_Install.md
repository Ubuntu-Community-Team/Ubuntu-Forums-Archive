---
title: "Ubuntu Install"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by readeano on 2008-02-08
hi all,

sorry if this has already been covered a million times but please be nice i am new. lol

Basically i have never used or installed Linux and guess what i have today and install ubuntu 7.1, i have now got to the dos like screen where it says username and password type that in correct and then it shows me similar stuff to command prompt, what do i do next so i can start using linux?

Thank you in advanced

James

---

### Post by emarkd on 2008-02-08
It should have booted directly into a graphical login screen.  Did you get the normal version or the server version?  If you got the server version, there is no GUI installed.  You can install it, however, by running

```
sudo apt-get install ubuntu-desktop
```

That's assuming your internet is up and working

---

### Post by jan quark on 2008-02-08
emarkd is right you probably installed the server version that can happen

do as emarkd suggested

or download the live aka desktop CD for a graphical installation or the alternate CD for an easy text mode installation

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

download the latest 7.10 version

---

### Post by readeano on 2008-02-08
i am not plugging it into the lan yet untill i have everything sorted! so do i need to be connected first  before i can procedd to the next step.

and yes i do have the  server version!

---

### Post by emarkd on 2008-02-08
Yeah, you can't install new software unless you're online.  The apt-get line I gave you above will connect to the Ubuntu software repositories and install what you ask for.

Or you could just use it without the GUI ;)  That works for some people.

---

### Post by readeano on 2008-02-08
tell you what, i shall try the download jan quark above suggested, it sounds easier, and also says deskto pwhich is what i guess im after.

cheers all will keep you all posted, 4% of download complete only 1 hour to go lol

James

---

### Post by jan quark on 2008-02-08
you probably have another internet connection because we are chatting here nicely

download the Desktop or Alternate CD and we are back on track again
see post above

:)

---

### Post by emarkd on 2008-02-08
> **readeano said:**
> tell you what, i shall try the download jan quark above suggested, it sounds easier, and also says deskto pwhich is what i guess im after.

cheers all will keep you all posted, 4% of download complete only 1 hour to go lol

James

That's probably the best way to go.  If the server functions are what you're after, you can easily install those as well by going to Synaptic at System > Administration, click on Edit > Mark files by task... and select LAMP server.  It's quite easy and you'll understand that better when you get your desktop up and going.

---

### Post by readeano on 2008-02-08
hi,

might have a slight problem here, have download desktop install and when i press install it says error reading disk, so of course i downloaded it again still same problem, just waiting for alternate download to finish!

James

---

### Post by jan quark on 2008-02-08
did you followed this guide to burn an iso image correctly ? :)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by emarkd on 2008-02-08
Did you verify your download?  You can get the md5 hash from the ubuntu site.

Otherwise, did the Live CD boot into a GUI?  And what is the exact error message?

---

### Post by readeano on 2008-02-08
no i had not, but because i am at work, secondary school, we are not allowed to use bit torrent! blocked by hampshire county council, it sucks. any other way i can do this?

---

### Post by readeano on 2008-02-08
> **emarkd said:**
> Did you verify your download?  You can get the md5 hash from the ubuntu site.

Otherwise, did the Live CD boot into a GUI?  And what is the exact error message?

restarted pc, and came up with the ubuntu install list i.e what install do you want to do? i clicked the top one being start install, and then error came up saying " error reading boot cd" "I/O error"

any suggestions

---

### Post by dstew on 2008-02-08
Sounds like a bad CD. Make sure you verify the hash on the downloaded ISO before burning, and then burn at a slow speed.

---

