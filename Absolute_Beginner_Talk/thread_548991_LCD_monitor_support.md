---
title: "LCD monitor support"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by lehi23 on 2007-09-12
I Have an Sceptre 16 :9 LCD Monitor with a native/max resolution is 1600 x 1050.  Right now the max resolution that I can get in ubunru is 1024 x 768.  How do I get ubuntu to allow higher resolutions.  I am very new to unbuntu and have used windiws all my life, but I am so disapionted in MS very beta release of Visa, that I thought I would this a try.  I am an absolute newbee so you will have to baby step me through it 
Thank you 
lehi23

---

### Post by BrendanM on 2007-09-12
Unfortunately configuring graphics cards in Ubuntu is still a bit tricky. The next version of Ubuntu which comes out in October should simplify this process a lot.

Anyway, you're going to have to add the resolution you want to the /etc/X11/xorg.conf file, which is a file that tells the GUI about your graphics and such.

You can check out some information here: [http://www.linux.com/feature/118108](http://www.linux.com/feature/118108)
and here: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Basically, you'll want to look for a section like this:
```
 SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
```

And add the resolution you need there. You'll need to do **sudo gedit /etc/X11/xorg.conf** to edit the file. Before you do, though, you should save a backup copy by doing **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup** then if anything goes wrong and your graphics won't start, you can restore the backed up version by simply typing **sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf** from the command line.

---

### Post by Brightbelt on 2007-09-12
Hi Lehi23,
Welcome to Ubuntu. First it's worth trying the easier approach. What might work is for you to enable what we call the restricted driver for your video card. 

You can find out what type of video card you have by running 'lspci' (without quotes) in your terminal,whch can be found thru the Applications menu/Accessories.

Go to your Restricted Drivers Manager, which is found through the System Menu/Administration/Restricted Drivers Manager.

There may be a box there which you can check which will enable your restricted driver. You'll need to restart your computer for it to take effect. 

There is a chance that your Graphic User Interface might crash as a result. If that happens, reboot and choose 'Start Ubuntu in Safe Mode' and come back to the forums here and people will guide you from there.

Good Luck, Frank B.

---

