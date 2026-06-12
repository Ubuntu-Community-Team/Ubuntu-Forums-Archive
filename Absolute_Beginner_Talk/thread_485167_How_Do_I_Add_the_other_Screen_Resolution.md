---
title: "How Do I Add the other Screen Resolution?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by justaname on 2007-06-26
When I loaded the server version of ubuntu 7 I only chose one screen resolution to install.  Now I realize I need a higher resolution. 

Is there a way to load one or more of the other resolutions, or do I have to reload ubuntu?

Thanks.

---

### Post by overdrank on 2007-06-26
> **justaname said:**
> When I loaded the server version of ubuntu 7 I only chose one screen resolution to install.  Now I realize I need a higher resolution. 

Is there a way to load one or more of the other resolutions, or do I have to reload ubuntu?

Thanks.

Hi you can use this command in the terminal *gksudo gedit /etc/X11/xorg.conf* and add the resolution that you want to each line under screen.:popcorn:

---

### Post by Rocket2DMn on 2007-06-26
The typical command for resetting the screen stuff is
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Here you will be given the option for video driver and screen resolutions - you can tab through the resolution options and hit spacebar to enable (on the correct screen, of course).  The command will take you through other stuff as well - read it, but you can mostly take default settings - it's pretty straightforward.

EDIT: overdrank's option is a simple way to go about what I mentioned, but many people have found it to not be as effective.  Give his a try first, and restart the Xserver (Ctrl+Alt+Backspace), if it doesn't work, do the reconfigure I mentioned.  

DO make a backup of your xorg.conf file before proceeding.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by greg_g on 2007-06-26
Read only if you want to read what everyone else has said, looks like we were all typing at the same time.  -greg



Here is a good how-to on the subject.  The first part about "running the autodetect script again" will help.

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

If you want a more "hands on approach" you can always edit the xorg.conf file by hand.  It is located in /etc/X11/xorg.conf   Of course backup the one you have now first "sudo cp xorg.conf xorg.conf.backup"

Then, you can open it with gedit "sudo gedit xorg.conf" and find the places where the resolutions are set.  Again, the howto does  a pretty decent job of explaining what it is you are looking at.  The part about editing the xorg.conf is about half-way down.

And if you find that you can't get back into your desktop, hit CTRL-ALT-F1 and it will bring you to a command prompt.  From there login then go "sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" (assuming the backup file is the name I suggested above) to put your old configuration back so you at least have a working computer.

Good luck!

greg

---

### Post by hanzj on 2007-07-05
I wish there was an easier, more newbie-friendly way to add a "Screen Resolution". I've tried 
> sudo dpkg-reconfigure xserver-xorg
but for that I have to go through not only Screen Resolution stuf, but other stuff (mouse, keyboard, etc) that I don't remember nor want to think about.

---

### Post by coolen on 2007-07-05
Did I read correctly...you have the server edition?
As in, the one with no GUI, right? Pure console goodness?
SSH into the machine from another computer with a GUI, then resize the window. SSH is far easier for accessing a server machine anyway.
If you're having trouble reading the output of certain commands, pipe it through less:
```
command_you_ran | less
```

---

