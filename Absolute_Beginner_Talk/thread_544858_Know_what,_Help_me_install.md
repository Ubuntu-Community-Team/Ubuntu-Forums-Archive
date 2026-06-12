---
title: "Know what, Help me install"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-09-06
Hi: I am trying to install js2mouse from here [http://cedric.vincent.perso.free.fr/Projets/index.html](http://cedric.vincent.perso.free.fr/Projets/index.html)
I have tried the guide on the website . I have the tar.gz on the desktop , how do i install it ?
I know very little about linux but trying to learn . Iam a Quad. with no finger movement so joystick 2 mouse helps me . I will add a screenshot.  Step by Step would help.
Thank you Jerry

---

### Post by louieb on 2007-09-06
The instructions on the web site are precise and pretty much step by step. The two things you need to do first is install a package called **build-essentials.  **This will install compiler and other stuff you need for the websites instructions to work.
You can use Synaptic or aptitude to install it.

Another place to find how to install software that not in the repositories. is in the sticky thread [B]how to install anything.
[/B]If you have questions about installing build-essentials or js2mouse you will find the answer there. Good luck. I know it looks hard but you can do it.

---

### Post by qpieus on 2007-09-06
To add to louieb's post, the **how to install anything** thread is at:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

see the "Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)" section about halfway down the page. It  takes you through the steps to build and install the application. It even has screencasts to looks at.
Have fun building!

---

### Post by jryprt on 2007-09-07
I am stuck , I installed Build-essentials , And did what is said in  How to install anything.
I took a screenshot . What Iam I doing wrong. 
Thanks you
Jerry

---

### Post by Steve1961 on 2007-09-07
OK, what you need to do is this:

cd js2mouse/js2mouse
make
sudo make install

There's a read me in the docs folder of the download that gives further instructions should you need them

---

### Post by jryprt on 2007-09-07
> **Steve1961 said:**
> OK, what you need to do is this:

cd js2mouse/js2mouse
make
sudo make install

There's a read me in the docs folder of the download that gives further instructions should you need them

Thanks Steve1961 that installed it . Now to make it work .
Thanks Jerry

---

### Post by CapnGimp on 2007-09-07
he needs help getting it to WORK.  There is something about changing Xorg.conf in the docs inside the tarball. He does NOT know how, is new to linux. Can someone help?
[http://sci.rutgers.edu/forum/showthread.php?p=714522#post714522](http://sci.rutgers.edu/forum/showthread.php?p=714522#post714522)

---

### Post by Steve1961 on 2007-09-08
Ok here goes then.  I've never used one of these so this is what I would try based on the instructions.

sudo gedit /etc/X11/xorg.conf

In this section I would add an entry called Mouse2, e.g.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Mouse2" "SendCoreEvents"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection


Then after the section for the configured mouse I would add this:

Section "InputDevice"
		Identifier  "Mouse2"
		Driver      "mouse"
		Option "Protocol"    "ImPS/2"		
		Option "Device"      "/dev/j2m_fifo"
	        Option "ZAxisMapping" "4 5"	
		Option         "Emulate3Buttons" "true"
	EndSection

Good luck :)

---

