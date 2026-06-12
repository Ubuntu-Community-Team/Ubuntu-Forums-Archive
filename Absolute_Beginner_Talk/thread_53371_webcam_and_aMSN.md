---
title: "webcam and aMSN"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by torkilmoe on 2005-07-31
Hi.
First, does anyone know any driver for Mtek (zeca) webcam mv402 that i can use in ubuntu? and is there any way i can chat with webcam in some sort of msn?

Thnx:)
Mvh Torkil

---

### Post by epukinsk on 2005-07-31
[QUOTE=torkilmoe]Hi.
First, does anyone know any driver for Mtek (zeca) webcam mv402 that i can use in ubuntu? and is there any way i can chat with webcam in some sort of msn?

Thnx:)
Mvh Torkil[/QUOTE]
 I did a google search for >mv402 linux< and it shows up on some supported hardware lists and it appears as a "Known OV511-based camera" in the Linux Kernel source:

  [http://glide.stanford.edu/lxr/source/drivers/usb/media/ov511.c?v=linux-2.6.5](http://glide.stanford.edu/lxr/source/drivers/usb/media/ov511.c?v=linux-2.6.5)

So I would guess that there is some level of support, though I can't test it because I don't have your device.

As for msn-like software, you can try [http://www.gnomemeeting.org/](http://www.gnomemeeting.org/)

It uses the H.323 protocol, so you can use it with any other software that supports that protocol.  In practice, this means you can use it on Linux and video chat with people on Windows using LiveMeeting (though the livemeeting people have to download an additional plugin).

I would guess that this is an intermediate to advanced task.  Meaning it would probably take me a few days to get working, and I have been using Linux for several years.  But you might get lucky. 

Anyway, that's all the help I can offer.  Someone else might be aware of applications that I don't know about.

Erik

---

### Post by arunsub on 2005-08-01
Latest Amsn nightly has video cam support. I downloaded and installed it, but since I couldn't get the driver for my webcam, I wasn't able to use that option.
 :mad:

---

### Post by tymek666 on 2005-08-01
[QUOTE=arunsub]Latest Amsn nightly has video cam support. I downloaded and installed it, but since I couldn't get the driver for my webcam, I wasn't able to use that option.
 :mad:[/QUOTE]
Which version of amsn have you download? I mean the version with video support....

---

### Post by arunsub on 2005-08-01
[QUOTE=tymek666]Which version of amsn have you download? I mean the version with video support....[/QUOTE]
I have installed 0.95b. I couldn't get to the home page of amsn.sourceforge.net to get you the links. You can find the link once you go to their homepage.

---

### Post by tymek666 on 2005-08-02
I think this 0.95b is some kind of beta version. On the official amsn site is only 0.94 avaible, unfortunately without webcam support :(

---

### Post by arunsub on 2005-08-02
[QUOTE=tymek666]I think this 0.95b is some kind of beta version. On the official amsn site is only 0.94 avaible, unfortunately without webcam support :([/QUOTE]
If you see my reply above, i wrote lastest Amsn nightly, which means it could be beta or alpha. Since the version says 0.95b, it should be beta.  :)

---

### Post by tahuya_rat on 2005-09-02
[QUOTE=arunsub]If you see my reply above, i wrote lastest Amsn nightly, which means it could be beta or alpha. Since the version says 0.95b, it should be beta.  :)[/QUOTE]

Hey,  man.  At the risk of sounding noobarific or something, could you be bothered to give a step-by-step on the install of the CVS snapshot?

It could really give me, in particular, a big break.  And then, next time a noobie like me asks for something like it, you wouldn't have to be bothered, because I could tell 'em.

TIA

tahuya_rat

---

### Post by arunsub on 2005-09-07
I did it few weeks back and don't remember now. I'm going to try that again soon. I can describe it better then. In the mean time try this. I took this from AMsn faq.

INSTALLING AND RUNNING
=====================

Q: What do I need to run amsn?
A: Amsn is written in tcl/tk, so you just need a working tcl/tk interpreter
(version 8.3 or later). You can get it at [http://tcl.sourceforge.net](http://tcl.sourceforge.net). The
interpreter is available for linux, windows and macintosh.Some additional
features might require extra programs or libraries, like the docking icon,
the Display Pictures or the SSL connection for MSN Protocol 9.

Q: How do I install and run amsn on unix/linux?
A: Just download the amsn-x_xx.tar.gz file. Untar it with the command:
  gzip -d amsn-x_xx.tar.gz
  tar xvf amsn-x_xx.tar
It will create an msn/ directory, and amsn is installed and ready to run.
To launch it, do:
  cd msn
  ./amsn
or if this doesn't work, try
  wish amsn
If wish command doesn't exist, then you don't have tcl/tk correctly installed.
If "wish amsn" works, but "./amsn" doesn't, edit 'amsn' file and set the
correct path to 'wish' in the first line. By default it's set to:
/usr/bin/wish

Q: After downloading imagemagick, How do I enable Display Pictures?
After you installed imagemagick, go to the AMSN's Preferences dialog. There,
click on "Others". Go to a field named "CONVERT", and click the browse button.
Then go to the folder where you installed imagemagick, and select the
"CONVERT.EXE" file. 
The, save preferences and restart AMSN. Then go to preferences again, and
check that the option "Enable receiving Display Pictures from other users"
is enabled, as it was disabled automatically because CONVERT.EXE couldn't
be found.

Q: When I double click "amsn" file from a graphical file browser, like
konqueror or nautilus, it opens a text editor instead of running AMSN!
A: AMSN is written in tcl/tk, an interpreted language, so the "amsn"
file is just a text file with the program code. The file manager might
think it's a text file, so it will launch the text editor. To run AMSN
you should choose "Open with...", "Launch with..." or similar, and use
the program "wish" to open the file "amsn". Again, as seen in the
question above, if the "wish" command doesn't exist, you need to
install tcl/tk.

Q: How do I create a shortcut to amsn on my desktop?
A: 1.- Add an icon to your gnome/kde desktop or menu, that
launches the command:
/wherever/you/have/amsn/installed/amsn
 for example
 /home/yourusername/msn/amsn
 2. Other way:
 As root, create a link in /usr/bin to the amsn file
 ln -s /wherever/you/have/amsn/installed/amsn amsn
 This way, you can launch amsn by just typing 'amsn' from
anywhere.
 Then add an icon that launches the command 'amsn'.

Q: How do I get the Gnome/KDE docking to work?
A: You have to run 'make' inside the plugins directory, to build
the OLD GNOME1 plugin. You'll need gnome development libraries. When
the plugin is built, just run amsn and select Gnome Docking in the
options menu.
To build the NEWER freedesktop (Gnome2 and KDE3 compatible)
docking, read README file in plugins/traydoc.

If it doesn't work it could be due to tcl/tk doesn't exists or not the latest version. Go to the site mentioned above and install it. 
Another way to find what is missing is, after extracting it to a folder, go to that folder and do the following:
./configure
make
sudo make install
you might get an error with what is missing in one of those steps.

---

