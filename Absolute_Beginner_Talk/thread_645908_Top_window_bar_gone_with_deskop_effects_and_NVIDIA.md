---
title: "Top window bar gone with deskop effects and NVIDIA Quadro?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Zoltarp on 2007-12-20
I had the top window bar disappear every time I tried to use Desktop Effects. I looked for a solution and found none. I know others were and probably still are looking for a fix too.

I found a solution that is very easy and straight forward. 

1. Disable your restricted driver under SYSTEM > ADMINISTRATION > RESTRICTED DRIVERS MANAGER ( uncheck the box ) then restart.

The following instructions were found here: [http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/)
It worked just fine for me in Gutsy. Basically you are just getting rid of the old NVIDIA driver and installing the latest.

The Process:

   1. Open a terminal and type sudo apt-get update
   2. Type sudo apt-get install nvidia-glx
   3. Type sudo apt-get upgrade
   4. Type sudo dpkg-reconfigure xserver-xorg
          * Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration
   5. Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
   6. You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes)
   7. You can also type glxgears to watch your card at work

I was then able to re-enable the desktop effects by right clicking on the desktop and selecting change desktop background then selecting visual effects and then checking the extra box. 

After you do that it will say you need the restricted NVIDIA drivers and it will then download the latest driver and install it. One more reboot and you should have your desktop effects and a menu bar too! Yeah! Hope that helps you too.

---

### Post by ajmorris on 2007-12-20
hi,
can you please start compiz fusion through a terminal (compiz --replace) and post the output.
Also, can you try emerald --replace in a terminal and post the output.

---

### Post by Zoltarp on 2007-12-21
I would like to be able to show you how to do that but I am a noob too. I'm now just learning a few things which I thought I would share (above).

I am sure if you create a new post you will get some help.

---

