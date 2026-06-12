---
title: "How to change video drivers?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-06
If I wanted to try a different nvidia driver, should I uninstall the one that is currently on the system first?  Should I disable restricted mode before installing another version?  Or can I just install the new on "on top of" the one currently installed?

Thanks.

---

### Post by Pigsflew on 2007-05-07
if you open up a terminal and enter
```
cat /etc/X11/xorg.conf | grep Driver
```
there should be one that says either "nv" or "nvidia". If you want to change it to another driver, you can edit it in this same file:
```
sudo gedit /etc/X11/xorg.conf
```
hit 'ctrl+f' and find "nv" or "nvidia", you should find that Driver line. You can change it to another driver if you choose. You don't have to remove the nvidia proprietary drivers from the system this way.

If you would like to remove proprietary drivers anyway, the easiest way is to go to System->Administration->"Restricted Drivers". There should be an item in there that says something about nVidia Accelerated graphics driver, you can just uncheck it from here and it will uninstall for you. Similarly, if you ever want to switch back to it, you can use this dialog box to enable it.

Once you have made either of the above changes, you will have to restart (or at least restart X).

---

### Post by timzak on 2007-05-08
> **Pigsflew said:**
> if you open up a terminal and enter
```
cat /etc/X11/xorg.conf | grep Driver
```
there should be one that says either "nv" or "nvidia". If you want to change it to another driver, you can edit it in this same file:
```
sudo gedit /etc/X11/xorg.conf
```
hit 'ctrl+f' and find "nv" or "nvidia", you should find that Driver line. You can change it to another driver if you choose. You don't have to remove the nvidia proprietary drivers from the system this way.

If you would like to remove proprietary drivers anyway, the easiest way is to go to System->Administration->"Restricted Drivers". There should be an item in there that says something about nVidia Accelerated graphics driver, you can just uncheck it from here and it will uninstall for you. Similarly, if you ever want to switch back to it, you can use this dialog box to enable it.

Once you have made either of the above changes, you will have to restart (or at least restart X).

Okay, I tried following your directions but could not see how to change driver versions from xorg.conf (there was not obvious, intuitive way to change driver revisions that I could tell).  So I disabled the restricted drivers, went into Synaptic, and downloaded the drivers I wanted to try from there.  They were the nvidia-glx-new (97.55).  After following instructions in Synaptic, I rebooted again and the screen still looked like it did when I disabled Restricted Mode drivers (ie, low resolution, goofy refresh rate, screen not centered) so I assumed the new 97.55 drivers did not take.  From this point I made the mistake of re-enabling restricted mode drivers and now I boot into some weird DOS-like blue screen with a bunch of text about Xorg.  I admit I probably went too far in veering away from your instructions, but how do I get out of this?  Is there a way to repair this without having to reinstall Ubuntu?

Thanks.

---

### Post by Pigsflew on 2007-05-08
Oh, sorry, I misunderstood. You'd like a different version of the same driver installed?

The "Restricted Drivers" should be the actual nVidia drivers, right?

You can gain back some measure of control when if Xorg breaks like that by hitting ctrl+alt+F2. This will switch to a terminal; You can always switch through F2 through F8, and F7 is your graphical output screen.

If you can copy here what some of the errors Xorg gives you are, it'd be useful for trying to figure out what exactly is going wrong. But to get you back into Gnome, Try switching to terminal 2 (ctrl+alt+F2) and using "sudo nano /etc/X11/xorg.conf". Find the section that says: 

```
Section "Device"
```

in this section, there should be a line which reads "Driver". This will be a specification of driver *type*, not driver version. If it says "nvidia", switch it to "nv". These are the open source drivers which have no 3d support, but are very stable. Once you've made the change, hit Ctrl+O to write, and Ctrl+X to exit Nano.

Then restart the machine by entering ```
sudo shutdown -r now
```.

It should bring you back into gnome. Let me know if this doesn't work. If it does, in addition to the xorg errors, let me know what driver it was set to before, and if you can open your xorg.conf file in gedit and just paste it here in a code block, I could look through it and compare it to mine.

Also, what specific card is it? You can find out by entering ```
lspci | grep nVidia
```

---

### Post by timzak on 2007-05-08
Thanks for the response.  I'm at work right now and can't try this til I get home tonight.  In the meantime, I will try to provide you with anything I know currently.

First, I have an EVGA 6800GS AGP.  The earliest driver revision for Windows that supports this card is 84.21. This is a relatively new video card (the AGP version was first released in January of 2006).  I am very proficient with computer hardware in general and in Windows operating systems, but this is my first foray into Linux, so if I sound like an idiot, it's because I'm trying to translate everything into Windows-speak.

Second, here is what I was attempting to do.  With the restricted mode drivers (I believe they are numbered 96.xx if you check the details of them in Synaptic) I was getting buggy performance with Desktop Effects and Beryl (missing top bars in all windows, blank Terminal windows (no text visible at all), etc.  So I thought I would try a different driver revision to see if it would help stability with Desktop Effects/Beryl.  This is why I wanted to load and try the newest nvidia drivers (nvidia-glx-new in Synaptic).  Synaptic tells me the driver revision of these is 97.xx.  

It seems like I created a driver conflict.  Perhaps both drivers are trying to load?

I am new to Linux and its terminology.  When you say: "But to get you back into Gnome, Try switching to terminal 2 (ctrl+alt+F2) and using "sudo nano /etc/X11/xorg.conf" do you mean getting back to the GUI?  I'm not exactly sure what Gnome means other than knowing it has something to do with Linux.

I will print out this thread to take home with me tonight so I can refer to it while not having internet access.

Thanks for you help.

---

### Post by Pigsflew on 2007-05-08
Yep, Gnome is your Ubuntu desktop GUI.

I've had this problem before with Beryl; specivically the window decorator, Emerald, sounds like it's not loading properly, which actually isn't a problem with the graphics driver. I forget what I did. I'll look into it and come back to this thread a little later.

---

### Post by timzak on 2007-05-09
Sorry, I didn't get a chance to try your suggestions due to family commitment.  But I was able to jot down the jist of the error message:

```
API mismatch-the Nvidia Kernal module has the version 1.0-9755, but this X module has the version 1.0-9631
```

The 9755 version is the newest one available from Synaptic (nvidia-glx-new).

The 9631 version are the restricted mode drivers.

Thanks again for your help.  Hopefully I'll be able to try out your tips tonight.

Edit:  what I don't get is, if I disabled Restricted Mode drivers BEFORE I installed the nvidia-glx-new drivers from Synaptic, why is there a conflict?

---

### Post by Pigsflew on 2007-05-09
Ok, pulling this from Nythain in [this thread]("http://ubuntuforums.org/showthread.php?t=436240"):

> sudo aptitude --purge remove nvidia-glx-new nvidia-kernel-common xorg-driver-fglrx
sudo aptitude clean
sudo aptitude update
sudo aptitude install nvidia-glx-new

that should take care of removing any previous attempts at installing it, and remove the fglrx driver wich is an ati driver i have no idea why you have installed, and try to reinstall just the driver package you need... theoretically and hopefully

Once you're looking at your splattered Xorg error screen hit ctrl+alt+F2 and try entering those (but forget the fglrx part). This should update the kernel module for nvidia-glx-new, which should fix things.

---

### Post by timzak on 2007-05-09
Thanks so much.  I'm back up and running now.  I really appreciate it...have tons more questions but I'll post them in new topics to give others an opportunity so you don't have to feel like my personal helper anymore.  :) 

Thanks again,
Tim

---

