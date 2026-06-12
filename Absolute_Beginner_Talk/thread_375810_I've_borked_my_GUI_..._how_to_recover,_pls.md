---
title: "I've borked my GUI ... how to recover, pls?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-03-04
Hi, 

I'm new here, and have been playing around with various things.  Most recently was Beryl (I read the disclaimer, I knew the risks, etc..).  I'm not asking for support with Beryl, I just want my GUI back!

Anyway, here's what happened:

Installed Beryl - worked fine
Rebooted PC - long error message saying that it couldn't find any usable screens.
Reinstated sources.list file that was copied in Beryl installation - no effect
Removed Beryl completely - no effect

Still cannot access my GUI.

I can post the full details of the error message if they will help more.  I can still log in to linux through the terminal (CTRL+Alt+F1, etc) so it's not a complete write-off - I would just like to recover the GUI.

Thanks in advance

HG

(sys details: amd64/nVidia 6800 GT/Ubuntu 6.10)

---

### Post by Crakie on 2007-03-04
You'll need to tell us more, such as what kind of card/drivers you were using (Ati, Nvidia). In either case, this will work (from the terminal):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select the vesa driver. Performance will be lousy, but you will get a GUI to get the original drivers up and running again.

---

### Post by floke on 2007-03-04
what happens when you try these?

sudo startx

sudo /etc/init.d/gdm restart

sudo dpkg-reconfigure -phigh xserver-xorg

Could also try

sudo aptitude remove xerver-xorg xserver-xorg-core

And then reinstall the modules

sudo aptitude install xserver-xorg xserver-xorg-core

---

### Post by klein de usa on 2007-03-04
hi
does it come up to your user name and password ? 
if it does try clicking on, in the lower left corner of the login screen <options> then <select session> then <gnome>  <change session>  put your screen name in and pass word in then make default <make default> 
what video card do you have ?
maybe you have to reinstall the video drivers?

---

### Post by Her Ghost on 2007-03-04
Hi - thanks for the replies.  I am going to try your suggestions now (I'm on dual boot so I will have to go away for a while).

The full error message that I get from the debug screen that comes up when X fails to load is this:

```
failed to load module wfb
API mismatch: the NVIDIA kernel module has the version 1.0-8776 but this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

NVIDIA(0): filed to initialise the NVIDIA kernel module!  Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details

***Aborting***

Screen(s) found, but none have a usable configuration.

Fatal server error.
no screens found.
```

be back soon :)

---

### Post by Her Ghost on 2007-03-04
thank you all

the 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

worked and I am now back in with Vesa drivers.

This might be a silly question, but is it now just a case of reinstalling my nVidia drivers to continue?

---

### Post by Crakie on 2007-03-04
> **Her Ghost said:**
> thank you all

the 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

worked and I am now back in with Vesa drivers.

This might be a silly question, but is it now just a case of reinstalling my nVidia drivers to continue?

Yeah. Consider using Envy for that. You can find plenty of posts on it around here.

---

### Post by coolcalt on 2007-03-13
I've borked mine as well.  I'd like to be able to fix it instead of reinstalling, although it is an option.

I have Edgy and was trying to install beryl, I have an ATI radeon 9200 SE video card.  I did not upgrade the drivers when installing beryl and when I lit the fuse, it didn't make it off the launch pad.  I got some debugging screen where it said

[INDENT]fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No Devices Detected.[/INDENT]

I looked in  /etc/X11/xorg.conf  and I didn't know much about what i was looking for.  

It also said to restart GDM when that file was configured correctly.

I tried the above suggestions, so far I haven't made any progress.


so I don't get into the gui.  It hangs and gives me the debugging screens. I reboot and go to recovery mode and get the root terminal to play with.   

I tried all the commands listed above plus a few more.  I'm no farther ahead, and I think I managed to uninstall my xserver,

---

### Post by zeifertstc on 2007-03-14
I'm, personally, against using Envy for installation of Nvidia drivers. Envy is the program responsible for my original borking in the first place. apt-get installing nvidia-glx is a tried and true method of getting something nvidia to work. However, if you don't trust your own hand, another scripting program that does just this step would be (pause) Automatix2. As much as I have heard that people frown upon the use of Automatix2, it does work and hasn't broken an update when just nabbing the vid drivers. However, after using Envy, I'm afraid a system-wide re-install is in order. I can't stand having to re-install a driver every other boot.

I must add in, before I forget, that Envy <i>does</i> do a decent job of installing the ATi proprietary driver. My laptop is running fine using Envy's installation of ATi graphics. For some odd reason, though, my desktop system became crap once the Envy install of Nvidia drivers was complete. My display lags to one side without the driver, the auto-adjust sets it up right on my monitor/tv but it resets things for the windows half of my setup as well, so for now, I have to auto-adjust the screen every time I switch OS'.

---

