---
title: "GUI for Ubuntu Server"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by billybob_gandhi on 2007-03-20
Hi all,

I am a n00b, and not afraid to admit it. :confused: Let me first say, my experience with Ubuntu is way better than with Fedora.  My issue however is, I'm reading a lot of different conflicting information on implementing a GUI interface with Ubuntu server.  It appears possible, but when I did ($ sudo aptitude install xubuntu-desktop) and also ($ sudo aptitude install gdm) I'm running into some issues.  The first time I tried it, my computer froze up and wouldn't go any further past the login.  I didn't know what to do so I re-installed it.  After several attempts I was finally able to install Ubuntu again.  I tried it once more to get GUI going, but this time when I ALT+F7, I get a message saying, "The X Server is now disabled. Restart GDM when it is configured correctly."  Any suggestions? Thanks.

---

### Post by blendmaster on 2007-03-20
For server installations, you usually do not want to have a GUI on the machine. However, I understand that you are a beginner at server installs, so maybe using the typical desktop installation would work.

To do this, just use the Ubuntu installation CD (not the server CD), and then add your LAMP (Linux,Apache, MySQL, PHP) software package separately through use of the repositories. This should help you on your way to starting your server very quickly. With luck, you'll soon be able to do all of your management through a Command-Line Interface.

---

