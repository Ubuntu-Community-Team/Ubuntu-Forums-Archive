---
title: "Installing Nvidia Legacy drivers in Ubuntu"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by wulfhound on 2007-04-07
I was just going to post how I got this to work for my older (2003) Nvidia card. It's the onboard chip on the MSI K7N2 Delta-ILSR with nforce2. 

Download the Legacy driver for your computer here at the Nvidia site, and get the readme too, since it has instructions in it.

Make sure you have libc libraries installed:
sudo aptitude install build-essential

Make sure you also have pkg-config installed:
sudo aptitude install pkg-config

Here is my question:

Do you also have to install the xserver-xorg-dev package?
(Edited answer: Yes. Otherwise it complains that it can't find pkg-config even though pkg-config has been installed.)

So, also run:
sudo aptitude install xserver-xorg-dev

I think that has something to do with the kernel compiling for the Nvidia driver on mine, since it didn't find a suitable one online....

So anyway...after having done that, go to CLI by pressing alt-ctrl-F1....

Once there, login with your user/pass and then stop the GDM by using 
sudo /etc/init.d/gdm stop

Now you can cd to your desktop, or wherever you saved the driver from Nvidia. Mine was on my desktop, so I did
cd Desktop

Then I ran
sudo sh NVIDIA-Linux-x86-1.0-7184-pkg1.run

Hopefully you have all dependencies met now that you had the above installed, and it should go smoothly. Just follow the onscreen instructions. Then, it will kick you out of it back to the CLI, where you type:

sudo /etc/init.d/gdm restart

Login, and see if you have the Nvidia control panel installed. Now, you follow the instructions in the readme, where you go into Xorg....

Open your xorg.conf file by typing 
sudo mousepad /etc/X11/xorg.conf

Of course use whatever editor you want, I use mousepad...

Now, find where your xorg.conf file says under Driver: "nv" or "vesa" and replace it with "nvidia"

Now, straight from the Nvidia readme:
****
In the Module section, make sure you have:

        Load   "glx"

You should also remove the following lines:
      
        Load  "dri"
        Load  "GLcore"     
****

Save it, and restart X....do the alt-ctrl-F1 thing again and type sudo /etc/init.d/gdm stop, then sudo /etc/init.d/gdm restart. Login, and hopefully everything's cool.

Sandaili

PS I also had to add this to my xorg.conf file to get the results I needed:

Section "Extensions"
Option "Composite" "Disable"
EndSection

---

### Post by nudnik on 2007-04-07
> **sandaili said:**
> I was just going to post how I got this to work for my older (2003) Nvidia card. It's the onboard chip on the MSI K7N2 Delta-ILSR with nforce2. 

Download the Legacy driver for your computer here at the Nvidia site, and get the readme too, since it has instructions in it.

Make sure you have libc libraries installed:
sudo aptitude install build-essential

Make sure you also have pkg-config installed:
sudo aptitude install pkg-config

Here is my question:

Do you also have to install the xserver-xorg-dev package?
(Edited answer: Yes. Otherwise it complains that it can't find pkg-config even though pkg-config has been installed.)

So, also run:
sudo aptitude install xserver-xorg-dev

I think that has something to do with the kernel compiling for the Nvidia driver on mine, since it didn't find a suitable one online....

So anyway...after having done that, go to CLI by pressing alt-ctrl-F1....

Once there, login with your user/pass and then stop the GDM by using 
sudo /etc/init.d/gdm stop

Now you can cd to your desktop, or wherever you saved the driver from Nvidia. Mine was on my desktop, so I did
cd Desktop

Then I ran
sudo sh NVIDIA-Linux-x86-1.0-7184-pkg1.run

Hopefully you have all dependencies met now that you had the above installed, and it should go smoothly. Just follow the onscreen instructions. Then, it will kick you out of it back to the CLI, where you type:

sudo /etc/init.d/gdm restart

Login, and see if you have the Nvidia control panel installed. Now, you follow the instructions in the readme, where you go into Xorg....

Open your xorg.conf file by typing 
sudo mousepad /etc/X11/xorg.conf

Of course use whatever editor you want, I use mousepad...

Now, find where your xorg.conf file says under Driver: "nv" or "vesa" and replace it with "nvidia"

Now, straight from the Nvidia readme:
****
In the Module section, make sure you have:

        Load   "glx"

You should also remove the following lines:
      
        Load  "dri"
        Load  "GLcore"     
****

Save it, and restart X....do the alt-ctrl-F1 thing again and type sudo /etc/init.d/gdm stop, then sudo /etc/init.d/gdm restart. Login, and hopefully everything's cool.

Sandaili

If the proprietary drivers do not offer any more functionality than the Ubuntu version, you, and others in the same situation may (in future) want to try the following, which is far simpler, especially for a novice:

sudo -s
#password
sudo apt-get install nvidia-glx-legacy

That will install the pre-compiled Ubuntu driver which is optimised for Ubuntu by the development team. Usually just takes a minute or two and can be done from within the graphical interface with an open terminal.

---

### Post by wulfhound on 2007-04-10
> **nudnik said:**
> If the proprietary drivers do not offer any more functionality than the Ubuntu version, you, and others in the same situation may (in future) want to try the following, which is far simpler, especially for a novice:

sudo -s
#password
sudo apt-get install nvidia-glx-legacy

That will install the pre-compiled Ubuntu driver which is optimised for Ubuntu by the development team. Usually just takes a minute or two and can be done from within the graphical interface with an open terminal.

I like the Nvidia control panel very much, so I wanted to have it installed this way. Just wanted to post it up in case someone else wanted to do it this way too for an older computer. There are a lot of walkthroughs but some of them leave out commands (that newbies don't know by default).

Sandaili

---

