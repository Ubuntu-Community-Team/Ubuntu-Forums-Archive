---
title: "guys, for real."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by jessek. on 2008-04-18
this is so messed up.  I've looked through everything and spent hours on this.  i can't figure this out. 

I made the mistake of messing with "screens and graphics."

the resolution is totally screwed up, and i can't change it.  I'm totally unfamiliar with this stuff so be easy on me.  

i tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
it didn't help.  

the monitor settings are just plain wrong.  i don't know what else to tell you.  screen is all blurry.  

do you think its something with my nvidia driver?  i don't even know how to edit that.
nvidia-settings tells me that i'm not using nvidia x driver.  edit x configuration and restart x server.  
does that mean anything?  

i'm getting so frustrated.  i don't know what i'm doing.

---

### Post by PmDematagoda on 2008-04-18
You can try:-
```
sudo nvidia-settings --config enable
```
to see if you can use the Nvidia driver.

---

### Post by ad_267 on 2008-04-18
Make sure the nvidia drivers are enabled by going to System - Administration - Restricted Drivers Manager and then restart X and run "sudo nvidia-settings" in the command line and set your options, make sure you save the changes to the xorg.conf file.

---

### Post by anewguy on 2008-04-18
I have also seen more and more people having problems when they add -phigh on the dpkg-reconfigure.  It's supposed to make it automatic, but more problems seem to be cropping up.  I think people would be better served to leave off the -phigh and answer the questions manually.  Just my opinion, though!  :)

---

