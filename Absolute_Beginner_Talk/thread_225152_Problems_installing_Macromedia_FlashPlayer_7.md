---
title: "Problems installing Macromedia FlashPlayer 7"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-29
Hi
I can't get Google videos to run successfully in Ubuntu (6.06) despite having spent quite some time yesterday fiddling around (and posting here).
Right now, when I double click the video in the Google website, the Google video "framework" opens with (all) the available videos shown on the RHS.

However, double clicking on a particular video leads only to a minor amount of I/N activity and then nothing.....just a blank screen.

I have checked if the Macromedia FlashPlayer 7 is really installed. However, I am unable to locate ANY plugins folder in /etc/mozilla-firefox.
So, it seems that the two plugins (    *  libflashplayer.so
   and  * flashplayer.xpt) have not been installed. 

This is despite having downloaded the software, unzipped it and then run the installer from the file browser by double clicking on it and choosing Run in Terminal.

I am very lost here and hope that somebody can point me in the right direction?

Thanks
Paul

---

### Post by Ares Drake on 2006-07-29
you might try installing Flash player with Synaptic: flashplugin-nonfree.

---

### Post by viper on 2006-07-29
You might want to try Automatix.
Check this link out for a detailed exlanation :[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=automatix)

---

### Post by PaulFXH on 2006-07-29
Hi to Ares Drake and Viper
Thank you for your replies. I went ahead with both of your suggestions and, although I had no problems with the installs, I still cannot get Google Videos to function from Ubuntu (they work fine from Windows XP on the same machine).
Looks like I'm running out of options.
I think I might just wipe this drive and clean install Dapper and see if I have better luck the next time around.

Paul

---

### Post by bhoughton on 2006-07-29
Hi,

I too am having troubles installing the flash plugin for Firefox.  I have tried "sudo apt-get install flashplugin-nonfree" and am informed that the package doesn't exist.  Synaptic doesn't find it in its package lists.  I have tried letting Firefox download/install it after loading a site that needed it and it fails.  Do I need to set up a special repo for it?

Regards,

---

### Post by Phen0m24 on 2006-07-29
same boat.  It says there is an error with the x11 fonts.

But when I try to install those they don't work either.

---

### Post by PaulFXH on 2006-07-29
Hi
Well, I still haven't persuaded FlashPlayer to work for me BUT I CAN see the videos!!

How?? OK, I select the video in the Google site and click it again when the column of available videos comes up. At this point a Download option appears. I chose the Video/(something else) option and download it.
After the download, the video pops up in Movie Player with SOUND (which was my problem to start with).

OK, it's not exactly the same as the streaming videos but it's better than nothing (or maybe not in the case of some of the videos).
While, the download can be slow for the longer movies, you do have the advantage that's it's a lot easier to re-run the movies as they are all stored waiting to be used again.

Paul

---

### Post by bhoughton on 2006-07-29
Got mine to work... ended up going to a site that indicated the flash plugin was needed.  After FireFox failed to install it, I chose the manual option. This takes you to a download site (Adobe), gives you instructions (download it, extract it, close FF, in Terminal cd to directory of archive and enter a specific command).  A text based installer opens and runs in Terminal, and then after installation was complete it asks me to quit session.  After doing so, there weren't any other problems. I did do all of this as a normal user, not root.  BTW, it did mention the fonts and asked me if I wanted to install them.  I chose "y" and it seems to work.  

Hope this helps.

Regards,

---

### Post by shiellb on 2006-08-17
I must be lucky today.  I ran "sudo apt-get install flashplugin-nonfree" and it installed on the first try.

---

