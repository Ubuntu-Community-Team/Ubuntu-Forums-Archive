---
title: "Getting Started with a 700MHz eMac"
date: 2007-06-09
forum: Apple PPC Users
---

### Post by coupdetard on 2007-06-09
I will be up front that most of this is not really anything new that I have found out. If you have been doing research on this forum about getting Ubuntu up and running on an eMac then you know most of this. However, I felt that it would be easier for people if they had a post that gave answers to a number of problems up front rather than having to read and decipher a number of different posts as I did.

If when you try to start the Ubuntu Live cd on your eMac everything seems to load fine except you are left with a black screen and never get a desktop (You may or may not get the Ubuntu login chime, I have had both). This black screen is because the Xserver is failing to start up correctly as it doesn't have the proper information to make the monitor work. To fix this there are a couple of things that need to be done.

To get to the console from the black screen press: ctrl + alt + F1

This should bring up the console with the cursor at the prompt. From there:

```
 sudo nano /etc/X11/xorg.conf 
```

That should bring up the live cd's Xserver configuration file. If you received an error make sure that the 'X' in 'X11' is capitalized and that the line looks exactly like the one above.

There are two modifications that need to be made to the xorg.conf file to get the Xserver starting and despite a number of posts to the contrary, at least on the 700MHz eMacs you do not need to disable the "DRI" module.

First modification: Down towards the end of the xorg.conf file is the section labeled "Monitor" make it look something like this:
```

Section "Monitor"
              ...
          HorizSync            71-73
          VertRefresh          70-140
          Modeline "1280x960" 122.24 1280 1328 1424 1696 960 961 964 1002 +HSync +VSync
EndSection

```

The major things from above are changing the "HorizSync" and the "VertRefresh" along with adding the "Modeline."

Once this is done the next section down in the file should be "Screen" in here there is but one simple thing to do. Add "1280x960" where it is shown here:

```

Section "Screen"
              ...
              SubSection "Display"
                        Depth                 24
                        Modes                "1280x960" "1024x768" "800x600" "640x480"
              EndSubSection
EndSection

```

Once that is done press ctrl+o then [Enter] to save and ctrl+x to exit the text editor. Then enter this line at the prompt:

```

sudo killall -HUP gdm

```

This will restart gnome and the Xserver. If everything was done correctly the desktop should appear and you are ready to install.

I would like to thank all the previous people who posted on the forum about the problems with getting an eMac up and running with Ubuntu, especially bodek who posted the nifty "Modeline" that is really the key to making this all work and if you want to check out his original post it is:

[http://ubuntuforums.org/showthread.php?t=246129&page=2](http://ubuntuforums.org/showthread.php?t=246129&page=2)

about halfway down the page.

Finally, there are more modifications that can be done to make sure everything works in a number of different color depths and resolutions. If anyone needs help with that I will be experimenting over the next couple of days and will post again here with a couple of other helpful things to know about getting things working, or in one case the futility of trying to.

---

### Post by 3rdalbum on 2007-06-09
Coupdtard, could you please run these commands:

```
cat /proc/cpuinfo > cpuinfo.txt
cat /etc/X11/xorg.conf > xorg.txt
```

And e-mail the "cpuinfo.txt" and "xorg.txt" files to my address:
 @ubuntuos.com chris

(that is, put the "chris" before the "@ubuntuos.com")

This would assist me greatly in developing an Xorg screen detection script for Copland.

---

### Post by coupdetard on 2007-06-09
Hey 3rdalbum if you didn't already see, I sent off those files to you.Good Luck.

---

### Post by coupdetard on 2007-06-10
I did a few other minor modifications after I modified the things mentioned above. My current xorg.conf file is attached to this post and you can view it if you feel the need to. Another thing that is worth mentioning is graphics drivers.

Right after I got the xserver starting and I had my gnome desktop I went online to search for PPC graphics drivers from nvidia for the 700MHz eMac's geforce2 MX graphics chipset. I went to the nvidia website followed by the ubuntu forums only to have my worst fears confirmed. Nvidia does not support linux on the PPC platform. There seems that there is an effort out there in the linux community to code some home grown graphics drivers but as of right now I can't find much other than an online petition that, despite the fake pornbot postings, I signed. If you want to sign the link is:

[http://www.petitiononline.com/nvppclin/petition.html](http://www.petitiononline.com/nvppclin/petition.html)

If I did my research correctly if you have a newer eMac you are in the clear. The newer eMacs all have ATI chipsets and apparently ATI is cooler than Nvidia and actually supports their hardware on PPC Linux.

Oh and if you are unsure as to whether or not graphics acceleration is working for you enter:

```
glxgears
```

into the command prompt in a gnome terminal. If the gears that appear are spinning nicely and smoothly, it is very likely that graphics acceleration is working correctly, if not then it is not working.

Another, more direct, way to tell if you are getting graphics acceleration is to enter:

```
glxinfo | grep direct
```

This will give you a yes or no answer as to whether or not it is working. I can't remember exactly who posted that line but thanks to anyone that knows that line off the top of your head. Anyway that concludes my little consolidation of getting started with an eMac. I will be checking up here if anyone has any specific questions for me or if something is unclear.

---

