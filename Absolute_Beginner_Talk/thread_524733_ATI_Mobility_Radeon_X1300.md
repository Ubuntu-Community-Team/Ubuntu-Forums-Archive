---
title: "ATI Mobility Radeon X1300"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by xdwmx on 2007-08-13
Hello, I am trying to install Ubuntu 7.04 (x86 Edition) on my Acer Aspire 5103WLMi laptop. I have tried Ubuntu in the past and I would love to use it on my laptop, but I'm having some problems.

Ubuntu goes through it's boot process with no problems, until after the loading bar. The screen goes black and goes through further configurations. Everything gets an "OK" and then after a while I get an error stating "Failed to start the X  server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" and there are two options, "Yes" or "No". So I can't even get to the GUI.

This happens not only on Ubuntu but on all of the heavy distros that I have tried (Ubuntu, Fedora, Zenwalk ...).

So I'm guessing my card doesn't have strong Linux support by default?

Please help me get Ubuntu up and running.

Here are my laptops specs.

CPU: AMD Turion 64 x2 TL52 1.6GHz
Graphics Card: ATI Mobility Radeon X1300
RAM: 1GB DDR2
Screen: 15.4" (1280x800)

Thanks.

---

### Post by Hospadar on 2007-08-13
Well the problem is most likely that your video hardware is not installed properly.

I would try envy to get this working, you'll need a working internet connection to do this, so if your wireless isn't working by default, you'll either have to plug yourself in or manually configure you connection in your /etc/network/interfaces file.  manual configuration is a little tricky and you'll need to know some network info, but there are some good guides around on how to do this.

First off though, have you successfully installed ubuntu yet, or is this problem showing up on the livecd?  If it's the livecd, I would suggest downloading the alternate cd which has a text-based installer (it still installs the gui though) you can get that [here]("http://ubuntu-releases.cs.umn.edu/feisty/ubuntu-7.04-alternate-amd64.iso") or you can pick a different mirror off the download site.

now, assuming you have it installed, let's move on to using envy to get your drivers installed.  If when you start up, you get that same error message, do ctrl-alt-F1 to get to a text terminal.

Now, let's stop gnome so that the driver installation can run smoothly. ```
sudo /etc/init.d/gdm stop
``` /etc/init.d/gdm is the startup script that starts gnome and your x server, you could also "start" and "restart" with this script.

now assuming you have an internet connection (if you arn't sure it's working, try pinging google with a "ping www.google.com" you can ctrl-c to stop pinging at any time.  now let's install and run envy ```
sudo apt-get install envy
sudo envy -t
```this will give you a little text interface, you'll want to install the ati drivers, let it edit your xorg.conf file, and restart your xserver.  If for some reason you have to manually start the xserver, just do a ```
sudo /etc/init.d/gdm restart
``` ideally, this will now plop you into gnome, if you get the error message again, post the details when it asks you if you want to see detailed output.  if nothing at all happens (no flashing or anything) try doing ctrl-alt-F7 (this takes you to the virtual terminal where gnome resides).

give this a whirl and see how things go.

good luck!

---

### Post by schorsch on 2007-08-13
I have the same graphic adapter in my laptop and I got it to work with these

[instructions]("http://ubuntuforums.org/showthread.php?t=414194") .... they are available in the sticky section of the absolute beginner talk right on top ....:)

---

### Post by Goce on 2007-12-16
I have DELL Inspon 6400 with ATI Mobility Radeon X1300 and am having trouble to run Ubutnu  7.04. I just ordered Ubutnu 7.1 hoping that this version will have the driver for this video card? 
Cheers

---

### Post by schorsch on 2007-12-16
I have the same laptop with the same graphics adapter and the mentioned instructions worked in 7.04 and 7.10.... what is your exact problem?

---

