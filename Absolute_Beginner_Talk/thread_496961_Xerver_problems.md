---
title: "Xerver problems"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-07-09
I installed beryl and added some lines to my xserver.....I thought everything was working fine but when I did a full rebout I got this with a blue screen

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  WOuld you like to view the x server output to diagnose the problem"



I just want to find a way to get into it so I can undo the changes I made.  I can not get to recovery mode.  After I view the problems it drops me off at the comand promt area.  How do I get into the Xserver to change it?

Noah

---

### Post by sugarland2k on 2007-07-09
You can reconfigure your Xserver if you can get to a command line in Ubuntu/Kubuntu.  

Code 
dpkg-reconfigure xserffer-xorg

Answer the questions the best you can, most of the defaults will work fine.  This should get your graphic screen up and running.  Good luck!

Billy in Sugar Land

---

### Post by overdrank on 2007-07-09
> **nynoah said:**
> I installed beryl and added some lines to my xserver.....I thought everything was working fine but when I did a full rebout I got this with a blue screen

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  WOuld you like to view the x server output to diagnose the problem"



I just want to find a way to get into it so I can undo the changes I made.  I can not get to recovery mode.  After I view the problems it drops me off at the comand promt area.  How do I get into the Xserver to change it?

Noah

HI  then you need to reconfigure you xorg
by running this command
Code:

```
sudo dpkg-reconfigure xserver-xorg
```

Answer a few questions and you should be up and running after reboot
Code:

```
sudo shutdown -r now
```

__________________

---

### Post by nynoah on 2007-07-09
Thanks I am back up again now.

Noah

---

