---
title: "How I made Ubuntu work with an  NVIDIA 8800"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by kielcary on 2007-03-05
I'm a total newb, but here is my story :)

I had a Nvidia 7900 on hand, so I was able to install with this card in. I'm going to assume there's an easier way to do it from the command line, but I tried everything I could and it just wouldn't work. So, my recommendation right now is to use another supported card, whether it is yours or you borrow it for someone else. If you can't find a supported card, download, install, and run Envy from the command line (I'm not sure exactly how to go about this as I am a complete and utter newb).

However, I DID get 6.10 running on an 8800 with the following steps:
To start, I installed 6.10 using the alternate CD (which allows a non-graphical install) with the supported card in. I didn't try the graphical installation with the supported card, but it would work I would imagine.

After installation, I ran Alberto Milone's Envy script from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). It was recently updated and the updated version didn't work for me. I downloaded the 0.8.2 version.

If the GUI version doesn't work for you (0.9.0) download this version (0.8.2), install it by double-clicking it, and then hit ctrl-alt-F1 to go to your terminal outside of GNOME. Log in, then type "envy" (no quotes). Select the first option. Even if you are given an error stating that your card is not supported, continue on.

After the script has finished and the new driver is installed, restart your xserver (the script will give you the option) to verify your installation.

Shut down your computer, put your 8800 in, and turn it back on. After the Ubuntu load screen, you should an NVIDIA splash screen, then you should be able to log in!

YAY! Right?

Wrong, sadly.

Now you need to update Ubuntu. There are roughly 10 xserver updates, important and recommended together, and when you update via the auto-updater one of these breaks the work you've just done.

When I restarted my computer, I made it to the Ubuntu boot screen. After that, a curser begins to flash in the top left hand corner and keeps flashing. The command line flashes at you a couple of times as xserver tries to start, and then you get the xserver's version of the blue screen of death.

Skip through this, it will take you back to the command line. Log in. Run envy again from the command line by logging in and typing "envy" (again no quotes please, heh)... and now it works

Hope this has helped someone... I almost gave up on Linux trying to get my 8800 working (I recently decided I hate MS enough to make the switch despite my software's dependency on that damn OS).


Things I haven't tried:
1.) Update using the supported card and then install and run Envy.
2.) Install using the text installer with the 8800 in, then download, install, and run Envy from the command line.

---

### Post by CaptSaltyJack on 2007-03-05
Could always run this script (found on the Beryl web site and modified it a bit).  And then your nVidia set up is also ready for Beryl too.

```
#!/bin/bash
if [ $UID -gt 0 ]; then
 echo "You must run this script as root.";
else
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
 echo "deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable" >> /etc/apt/sources.list
 wget http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg -O- | apt-key add -
 aptitude -y update && aptitude -y install linux-restricted-modules-$(uname -r) nvidia-glx
 nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by kielcary on 2007-03-05
Great!  I'll give it a try.

Planning on running Beryl, but as I said I'm a total newb.

---

### Post by CaptSaltyJack on 2007-03-05
Please read this and use their script if you plan on installing Beryl:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

---

### Post by kielcary on 2007-03-05
Will do -

If I follow the non-automated instructions, do I still need to use the script you posted?

---

### Post by CaptSaltyJack on 2007-03-05
I would recommend against the non-automated.. and I didn't take that route so I don't know how well it works.

Start here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Creating_the_script](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Creating_the_script)

Copy that code into a file, execute it.. and you're done. :)  Very easy on Ubuntu 6.10.

---

