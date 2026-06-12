---
title: "Cant watch video on TV Out"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by rubbsdecvik on 2007-07-08
Ok, so I got TV-Out to work on  my IBM/Lenovo T43 laptop, but the only way I knew how to get it to work was in clone mode.  If I try to watch a movie, it will show up on my laptop screen, but it only shows a black box inside the video viewer.  

I would prefer to leave things in clone mode.  I did try to make it a "big desktop" however, then I was forced to use a very small resolution on my laptop.  I have a Radeon Mobility M300 on my laptop.

Any help would be greatly appreciated.  I'm sorry if this seems kind of confusing.

Thanks,
Rubbs

---

### Post by TwistedLincoln on 2007-07-10
Cloning the display won't allow you to play video on the output.  It's like that in Windows also.

Don't know if it will work with the ATI card, but with my Nvidia card, I just switch between my monitor and my TV as the ONLY display.

First, I created an copy of my xorg.conf file, and named it xorgOUT.conf.  Then I created another copy called xorgLCD.out

Then I edited this xorgOUT.conf file as such:

[I]Locate Section “Device” 

Under the last option, add the following two lines:

Option "ConnectedMonitor" "TV"

Option "TVStandard" "NTSC-M"[/I]

After saving the file, I then created two scripts -- one to activate the TV out, and once to switch back to the monitor.  Basically, the scripts were just:

To activate TV Out:
[I]sudo rm /etc/X11/xorg.conf
cp /etc/X11/xorgOUT.conf /etc/X11/xorg.conf[/I]  

To get back to the LCD:
[I]sudo rm /etc/X11/xorg.conf
cp /etc/X11/xorgLCD.conf /etc/X11/xorg.conf  [/I]

Of course I had to chmod the X11 directory to allow this first...

Anyway, it isn't an ideal situation, because you only get the LCD or the TV, but not both.  But it does the job, and I can play videos just fine.

---

### Post by rubbsdecvik on 2007-07-10
Ok, that's fine, I was just wondering.  I think I'll try your script idea.

Thanks!

---

