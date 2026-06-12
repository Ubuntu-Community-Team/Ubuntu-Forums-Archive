---
title: "Screen Resolution problems"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by drtone on 2007-08-28
Hi there, 
I have just installed Ubuntu 6.06 lts on MSI mega 865 pro which is connected to a 39 inch lg screen as a media centre pc. 
fiesty fawn worked out of the box except during bootup the screen would go blank with two lines on it. if i switched the tv off then on again then it worked fine. Also when i shut down the pc ubuntu would shut down followed immediately by a restart.
so i installed 6.06 which has neither of these issues. the only problem i am having is that the screen resoultion does not give me an option above 640 x 480. 
i have tried xorg configuration edit and deleted all the resolutions that i did not want.... this did not work.
the video driver is an integrated intel 84865g chipset and the installed driver is i846 or something resembling that.
i tried downloading the driver from the intel site but couldn't install it. 
can someone help me either,,,,, fix the screen resolution or tell me how to get around the problems in feisty fawn. 

thanks.

---

### Post by stinger30au on 2007-08-28
try this

If your monitor is giving you a hard time and not showing the right resolutions this little trick may fix it
sudo nano /etc/X11/xorg.conf
scroll down using the arrow keys till you find this section
Section "Monitor"
at the bottom of this section add these two lines

HorizSync 30-110
VertRefresh 50-70

now quit and save and restart. with a bit of luck, should be all good!

---

### Post by s26c.sayan on 2007-08-28
In a terminal, try 
> sudo dpkg-reconfigure xserver-xorgThis will start an interactive dialog. Answer the questions properly, esp. those about the Horizontal Sync rate and Vertical Refresh rates for your monitor (look for these info in the hardware manual that came with your monitor or in the stickers at back of the monitor).
Restart X, and all should be fine.

---

### Post by lonce on 2007-08-28
Also, you can disable EDID in your xorg.conf.

The tv will send a nugget of info to your PC telling it what it can handle.  Sometimes it gets interpreted wrong.  If you tell it to ignore the EDID then you can pretty much set it to what ever you want.

Be careful though, without the EDID you can set it to something that would hurt the TV.  Just make sure that your TV can handle what ever resolution and refresh rate you want to use.

---

