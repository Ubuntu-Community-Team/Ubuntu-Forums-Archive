---
title: "change matrox g450 resolution"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by nhflyer on 2007-03-07
Finally succeded in getting choices in the resolution settings!!!!!  I have an old computer with an amd k2-400 and a matrox g450 dual head video card that was laying around.  After I installed Dapper (ubuntu 6.06) the only resoulution that I could get was 640x480.  I looked everywhere for a solution and finally found this solution.  

I followed the instructions at this link.     [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution) 

Open the terminal

Step 1.  Backed up the xorg.conf file
            code:  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Step 2.  Turned off xorg (gnome, the thing that controls the desktop)
            code:  sudo /etc/init.d/gdm stop

Step 3.  After the desktop disappeared. At the prompt. I Ran the automatic hardware configuration
            code:  sudo dpkg-reconfigure xserver-xorg

Step 4.  This will run the configuration.  It will guide you through all the devices. Video, Display, keyboard, mouse, etc.  I stayed with the defaults and at video section there was a place to select what resolutions should be used.  I selected 640x480, 800x600, 1023x768 at a color depth of 24.  ( I messed around a bit and just kept rerunning the guide until I got it right)

Step 5.  At the end of the configuration you're back at the prompt. Turn on the xorg (gnome)
            code: sudo /etc/init.d/gdm start

Step 6.  If it worked you'll get the desktop if not you'll get an error message.  Try it again.

When gnome reloaded I had all three resolutions available in the Screen Resolutions.

I hope this helped.  I just flogged my way through this one and got it to work.

This is my first post so I make no claims to my typing accuracy.  Refer to the link site and copy and paste the text to be sure.  Also, I found that at the prompt you can use the arrow keys to index through prior entries so you don't have to type them again.

---

