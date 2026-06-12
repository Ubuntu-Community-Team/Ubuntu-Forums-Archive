---
title: "[SOLVED] Display problems"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-07-12
I am having problems with my display.  My computer is a Dell XPS M140 with an integrated Intel Graphics Media Accelerator 900 graphics card.  I have looked and I can't find how to change my display size.  When I go to System -> Preferences -> Screen Resolution I only have one choice for the Resolution, 1024x768.  If anyone can help that would be awesome.

---

### Post by Rocket2DMn on 2007-07-12
Ahh, a classic problem, run this in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
write this command down, you will use it a lot if you fiddle with your video stuff.
When you make your way through the configuration, please read so you know what's going on (don't just ENTER your way through it).  When you get to the resolution page, hit TAB to cycle through and SPACEBAR to select your monitor's max resolution and everything less than that.
Let us know if you have further problems.

---

### Post by slughappy1 on 2007-07-13
I tried that, and answered the questions to the best of my knowledge.  But when I rebooted Ubuntu wouldn't start.  It came up with an error saying that my display settings in  /etc/X11/xorg.conf were not set up properly.  I made a copy of the file before hand just in case and had to replace the new with the back up.  Can you tell me what I did wrong or do you need more information as to what I entered?

---

### Post by User X on 2007-07-13
I had the same problem initially because I changed my display driver to the ATI driver (I have an ATI card) however Ubuntu didn't like it.  I changed it back to what it was initially, and only made changes to the display resolution section of the menus and this fixed my problem.  I am very new so please don't take anything I have to say as gospel but, this worked for me.

---

### Post by Atomic Dog on 2007-07-13
Open synaptic package manager (System-->Administration).

next click the search button and enter "xorg-video-intel" Install. This should work.  Reboot and see what happens.

---

### Post by bumanie on 2007-07-13
I had a similar problem. You may have to go to system administration and go into restricted drivers. There you will find propriety drivers for nvidia and ati. Once installed you should have more resolution options.

---

### Post by Rocket2DMn on 2007-07-13
I agree with AtomicDog's approach, it sounds like you need different drivers, possibly restrict ones.  Give it a go and let us know how it works out.

---

### Post by charge1 on 2007-07-13
Try below:

Intel Graphics driver (i810) won't use high screen resolutions

There is a common issue with Intel graphics resulting in screen resolutions not being available even after adding them to the xorg.conf file. This happens with the i810 video driver, but the newer intel driver does not have this problem.
Install newer modesetting Intel video driver

Unfortunately the newer driver is only available from 6.10 onwards (Edgy, Feisty etc), but not in 6.06.1 (Dapper). If you have Edgy or above then you can install the newer intel video driver with:-

sudo apt-get install xserver-xorg-video-intel 

Then edit your /etc/X11/xorg.conf and change the

Driver "i810" 

to

Driver "intel" 

You can edit the xorg.conf from the command line using

sudo nano /etc/X11/xorg.conf 

Alternatively from withing the GUI using

ALT+F2 
gksudo gedit /etc/X11/xorg.conf

---

### Post by slughappy1 on 2007-07-16
Well on further exploration of the forums I saw someone mention installing 915resolution.  I tried it and it added one more resolution size.  I now have 1280x800 and 1024x768.  Although it would be nice to have more than just two options.  I will try what you guys said and see if I get any more.  I'll get back on tomorrow or the next day to tell what adventures I had.

---

### Post by slughappy1 on 2007-07-17
Weirdest thing, I installed the xserver-xorg-video-intel and then tried to change the display size.  It then acted like I pressed ctrl+alt+backspace.  So then I edited the xorg.conf file and replaced i810 to intel and tried to change the display size again.... It did the same thing.  Although I have many more options now:

1280x800     (This is the only one that works, all others restart X)
1280x768
1024x768
800x600
640x480
1280x1280

---

