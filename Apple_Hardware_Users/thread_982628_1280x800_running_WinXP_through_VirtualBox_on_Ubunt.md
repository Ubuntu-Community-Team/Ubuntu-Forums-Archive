---
title: "1280x800 running WinXP through VirtualBox on Ubuntu OS on my MacBook"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by timchesonis on 2008-11-14
I have a MacBook, (white version), 13" screen, 1280x800 screen resolution.  Ubuntu works perfect on it.  There are, however, two applications that I must use on Windows, (I have WinXP), and these two applications do not work under Wine.

I use VirtualBox to load Windows XP.  Great program, (and free).  However, When loading Windows through VirtualBox ON UBUNTU, I do not get a 1280x800 option, (I get 800x600 all the way up to 1600xsomething), but no 1280x800 (which is the full screen display on my MacBook.

Now, the weird thing is that when I run VirtualBox through the Mac OSX, I am able to use, "Seemless Integration".  Please tell me how to get "Seemless integration" to work on my MacBook.

---

### Post by timchesonis on 2008-11-15
SOLVED:

I must share how I resolved this issue because I love Ubuntu, and I'm growing to enjoy this community, so let me give something back.

The first thing I need to share is that my Xorg.conf file has nothing to do with the solution to this problem.  Ideally, I wanted to get the "Seamless Integration" implemented.  My problem was that I could not get the seamless integration implemented, until I read this phenomenal article (link posted below).

[http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/](http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/)

It was here that I discovered that I needed to unmount the CD drive, and THEN click on "Install Guest", and sure enough it installed, which then allowed me to load "seamless integration" on Ubuntu.

From that article, you can also learn how to configure a shared folder(s) between Ubuntu and Windows. Nice.  Very Nice.

The coolest thing is that I can now launch VirtualBox from my second desktop (screen), and then Windows on that desktop and then switch back to my Ubuntu Desktop at will.  Very nice.  Couldn't be happier.

Thanks for helping me learn more about Ubuntu, I hope that this has helped someone out there in my situation.

---

### Post by morphos on 2008-11-15
Congratulations! Solving problems on your own or through the forums only gets easier from here.

---

### Post by irish66 on 2008-11-16
Hi, would virtual box run on computer with 1 gig of memory, windows xp
M

---

### Post by timchesonis on 2008-11-16
> **irish66 said:**
> Hi, would virtual box run on computer with 1 gig of memory, windows xp
M

Yes, but it'd be slow.

---

### Post by irish66 on 2008-11-17
Thank you.
M

---

