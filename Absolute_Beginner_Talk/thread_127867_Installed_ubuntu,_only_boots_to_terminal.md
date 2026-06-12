---
title: "Installed ubuntu, only boots to terminal"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by napsilan on 2006-02-10
After the CD finished installing Ubuntu, the system rebooted to finish the installation.  However, when I booted into Ubuntu from GRUB, it just gave me a teriminal command line and no GUI or install finish.  Is there a command from the terminal that it boots to that will complete the installation?

---

### Post by Maelgwyn on 2006-02-10
what kind of installation did you do?
 
When the computer booted from the cd, did you just press enter, or did you type something like **server**?
 
If you did a server installation, you're going to have to track down the files you need to apt-get and install a GUI (plus something like GDM/KDM) from scratch...
 
Hope this helps!

---

### Post by r4ik on 2006-02-10
Type,
sudo apt-get install ubuntu-desktop

Good luck !

---

### Post by napsilan on 2006-02-10
I did an expert install for AMD64, but pretty much just hit enter for everything.  The one thing I know I needed to change was the video driver from autodetect to vesa.  I played around with live until that worked before I went to install it for real.  I will try that command, thanks.

Edit: Didn't work.  Entered that command, asked me for superuser password.  I entered it, but nothing happened.  Tried entering the command again and still nothing.  Also, 'sudo reboot' does the same thing (ask for pw, does nothing).  Should i just reinstall ubuntu?

---

### Post by r4ik on 2006-02-10
My pleasure.

---

### Post by r4ik on 2006-02-10
You can not see the paswd while typing just type it correctly and hit enter.

---

### Post by 3rdalbum on 2006-02-10
The installer uses different autodetection than the Live CD. For instance, I needed to manually set things to run the Live CD on my computer, but the installer had no troubles.

The command given earlier won't solve your problem; all that does is install the whole GUI package, which you probably already have. Have you tried typing "startx"?

If there's a problem with your video settings, typing startx will probably give you an error message, which should help you/us to find out what's wrong.

I think there's also a command that takes you through the video card/monitor setup... could somebody help me out here? I think it's "sudo x-org-reconfigure" or "sudo configure-x-org" or something like that.

---

### Post by r4ik on 2006-02-10
sudo dpkg-reconfigure xserver-xorg

Youre prob right the command isnt any use in this case my bad.

---

### Post by napsilan on 2006-02-10
startx and sudo dpkg-reconfigure xserver-xorg do nothing as well.  Seems like that terminal doesn't respond to much of anything.  I can use stuff like "ls" and "cd" to navigate around, but none of the commands you suggest do anything.  Just gives me an empty prompt on the next $> line (not password, i know that it doesn't show up).  The grub lists 4 different ubuntu's, regular, default, recovery, or recovery default, are those of any use?  I've been choosing regular.  Also, does the kernal I installed matter?  I chose the default one that was highlighted when I installed.  (k8 with no suffixes).

---

### Post by napsilan on 2006-02-10
Reinstalled ubuntu without doing expert mode.  Had to enter recovery mode to reconfigure the graphics driver but it's working now, posting from it now.

---

### Post by Maelgwyn on 2006-02-10
Awesome - I was going to suggest booting to recovery mode but you beat me to it! :)

Hope the system stays working for you :)

---

### Post by lenny45 on 2006-02-10
hey guys, i am trying to download the correct mirror site. do i download it straight to a CD for thr CD Live?

[http://ftp.osuosl.org/pub/ubuntu-releases/](http://ftp.osuosl.org/pub/ubuntu-releases/)
this is the first one on the cd list......what parts of this puppy do i download?
thx...

---

