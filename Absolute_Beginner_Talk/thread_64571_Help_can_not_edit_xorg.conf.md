---
title: "Help can not edit xorg.conf"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by msti on 2005-09-11
I have tried to install ubuntu twice on a PII 233 128K ram 4gig hd machine with an ATI mach64 video card. (Install takes over two hours). When I put in startx I get

(EE) ATI(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a usable configuration

When I try to edit the xorg config file with vim I find that it is read only.  I do not have root access.  What is the root password on a new install?  The installation disk only asked for a User account and password. I need to change the file attributes from read only to edit this file and set the bit depth to 16.  I selected 640 *480 for screen resolution on the second install.  This is the first time I have tried linux.  Access to information is extremely difficult. There were no manual pages for atimisc which should be the required driver. ATI site says ask linux community.

Is there a light version that I can get up and running?

---

### Post by aysiu on 2005-09-11
sudo gedit /etc/X11/xorg.conf

---

### Post by tseliot on 2005-09-11
[QUOTE=msti]I have tried to install ubuntu twice on a PII 233 128K ram 4gig hd machine with an ATI mach64 video card. (Install takes over two hours). When I put in startx I get

(EE) ATI(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a usable configuration

When I try to edit the xorg config file with vim I find that it is read only.  I do not have root access.  What is the root password on a new install?  The installation disk only asked for a User account and password. I need to change the file attributes from read only to edit this file and set the bit depth to 16.  I selected 640 *480 for screen resolution on the second install.  This is the first time I have tried linux.  Access to information is extremely difficult. There were no manual pages for atimisc which should be the required driver. ATI site says ask linux community.

Is there a light version that I can get up and running?[/QUOTE]
The password is the same you typed during the installation.

However if you need root privileges (and sudo doesn't work) restart your computer and keep on pressing ESC as soon as you see the word "Grub". Then select Recovery mode from the list. Now you can modify your xorg file without using "sudo" (etc).

---

### Post by Fluffy, the jolly sheep on 2005-09-11
Ubuntu doesn't have a real root account like many other linux distro's. You can use your user password for running programs which require root access. For running a command with root access you'll need to run: 
  sudo *command*
you will then be prompted for your (user) password.

Also, if you're unexperienced with vim, you might find the editor nano a bit easier to use. Then you'll need to enter 'sudo nano /etc/X11/xorg.conf'. gedit won't work because it requires the Xorg to be running

Once you can boot ubuntu, you might want to install something lighter than the gnome2 desktop, install e.g. xfce4 with synaptic. Before you can install it, you would need to add the universe repository: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by msti on 2005-09-11
Thanks for the help

I still can not get x started

(EE) ATI(0): Depth 16 is not supported through this adapter
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screens found

X10: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (o known processed) with 0 events remaining
xauth: (argv):1: bad display name "ubunto:0" in "remove" command

Do you have any suggestions?

---

### Post by tseliot on 2005-09-11
Try to set "vesa" instead of "ati" in your xorg.conf

---

### Post by msti on 2005-09-11
Thanks, I'll try this tonight and let you know if it works

Mark

---

### Post by msti on 2005-09-12
Thank-you

The "vesa" worked and I now get to the gui log in screen.  I have a serial mouse and am having trouble getting it recognized. I noticed in the boot post, the line -
mice: PS/2 mouse common for all mice

This even though I edited xorg.conf to reflect a serial mouse.  Any suggestions?

Also how do I run the gui from the keyboard?

---

### Post by tseliot on 2005-09-12
Turn on the computer and when you see the word "Grub" keep in pressing ESC.

Select Recovery mode from the list

after it boots to the command line type:

dpkg-reconfigure xserver-xorg

it will ask you several things(if you don't know the answer just press Enter):

Tell it to autodetect the card and then select "vesa".

At some point it will ask you questions about your keyboard and mouse.

It will ask you (I don't remember when) you desired resolutions:

select the one you need and press the spacebar to enable it (press Enter when you've finished)

When it comes to the refresh rate question select "advanced" and put the values of your monitor (horizontal and vertical refresh) if you know them, otherwise select the easiest and recommended mode.

[COLOR=Red]REMEMBER: when you don't know the answer to its questions just press ENTER (and the recommended answer will be chosen)
[/COLOR]
Then restart your computer. The computer will work now.

---

### Post by msti on 2005-09-12
Thank-you very much. I am now up and running and can start to explore.

Mark

---

### Post by tseliot on 2005-09-12
I'm happy everything works now. Enjoy your Ubuntu experience!  :wink:

---

