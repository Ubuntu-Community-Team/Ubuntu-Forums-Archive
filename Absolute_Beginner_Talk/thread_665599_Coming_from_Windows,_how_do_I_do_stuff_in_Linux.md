---
title: "Coming from Windows, how do I do stuff in Linux?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by raccoonone on 2008-01-12
I've been using Windows since Windows 3.1, and am disgusted with Vista so I want to give Linux a try. Is there a guide that explains, in depth, how to do equivalent things on Ubuntu? I read the brief guide in the Ubuntu documentation, but I'm looking for something more comprehensive.

In particular I would like one that covers the following questions: 
How do I rearrange things on the taskbar (like the power button)?
On Windows I can press Ctrl-Alt-Del and get a process manager, can I setup Linux to do this?
How do I install stuff that's not in the repositories? On Windows I just run a .exe, but Linux has this whole make/install thing, and then .rpm and .deb files which I don't understand

If anyone can point me to a guide, or answer my questions that'd be great!

---

### Post by Flying caveman on 2008-01-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

rearranging the panel is easy, just uncheck the lock to panel box then you can click on move to move it wherever you want.

there is a way to ctrl-alt-del to get to process manager but i can't remember right now.  It was pretty easy to do that but probably just as easy to add system monitor to the panel then click on that.

EDIT:  here's that ctrl-alt-del thing [https://answers.launchpad.net/ubuntu/+question/19234](https://answers.launchpad.net/ubuntu/+question/19234)

---

### Post by perlluver on 2008-01-12
Have a look at the two guides in my signature.

---

### Post by bwhite82 on 2008-01-12
.debs are the .exes of Debian and Debian-based distros (Like Ubuntu). .rpms are the .exes of RedHat and Redhat-based distros. However, in many instances, there are minor differrences between the Debian version of .debs and the Ubuntu version. Its best to stick with the the flavor of your distro.

---

### Post by SOULRiDER on 2008-01-12
> **Soldierboy said:**
> .debs are the .exes of Debian and Debian-based distros (Like Ubuntu). .rpms are the .exes of RedHat and Redhat-based distros. However, in many instances, there are minor differrences between the Debian version of .debs and the Ubuntu version. Its best to stick with the the flavor of your distro.

Instead of describing them as exe's i'd describe them properly by saying they are packages, some sort of 'installer'

When you want to install something that is not in the repos you will have to find a DEB package. Ubuntu DEBs are what you want but if you cant find one you can probably use a DEB package made for Debian. You will most likely be able to find one except for some rarely used applications. A good place to find deb package sis [http://www.getdeb.net](http://www.getdeb.net)

RPMs can be installed by using Alien although its not recommended. You can also install from source by compiling the program, then suing the checkinstall command to make a deb package (so  you can uninstall the program easily, most people seem to omit this step for some reason) and you're all set.

If you have any further questions just ask.

---

### Post by jasonrandolph on 2008-01-12
If you want to grab a book about doing such things, check out "Ubuntu for Non-Geeks".  It's cool because it is project-oriented and walks you through everything from installation to getting your iPod up and running in Ubuntu.

Beyond that, these boards are the most comprehensive knowledge base I know of.  And, as long as you're polite, everyone seems willing to help.

---

### Post by bagguley on 2008-01-12
Ive used Ubuntu exclusively now for about a year (to the point where I struggle to remember how to do things in XP and havnt got a clue about vista!). These forums are by far the best source of advice available on the web. I do however recommend the following site. It covers small things that you wouldnt necessarily occur to you, but make ubuntu so much more fun!

[http://epologetics.org/ubuntuhowto.php](http://epologetics.org/ubuntuhowto.php)

I also recommend trying the full compiz/beryl out. So nice!

---

### Post by raccoonone on 2008-01-12
Awesome thanks for all the help! I wasn't expecting to get some many detailed replies. The community here is really great.

One last question about games. I heard I can run a virtual Windows machine under Linux. Would that be a viable way to use my Windows applications that don't have a Linux alternative (games are the only thing I can think of right now), or will the performance be too slow and I should just dual-boot? My computer is fairly new, but most of the games I play are pretty old, so even if the performance was 25% of normal it'd probably still be fine. I looked at the Wine project, but only some of the games that I want to play work with it.

---

### Post by Dr Small on 2008-01-12
3D stuff doesn't work in VirtualBox, and the speed would be horrible if it could, so your best bet would be to dual-boot if you want games.

Dr Small

---

