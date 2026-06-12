---
title: "Dual-Screen Functionality in Kubuntu (ATI X1400) *Weird* Issues"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-03-27
Hey everyone.  I'm new to the forums, and relatively new to linux.  I'm officially living a Windows-free lifestyle now, and loving every minute of it.  I am running into a few setup questions, however.  I'm currently running Kubuntu (Gutsy) and have been trying to get dual-screen functionality working the past couple of days.  I'm running the distro on a ThinkPad T60 laptop with a ATI X1400 Radeon graphic card.  A few days ago I found a program called "Envy" which automatically detected my card settings, installed, and edited the xorg.conf file accordingly.  It seemingly worked correctly after I restarted.  However, when I would try to shutdown/restart from the GUI it would freeze up at a blank screen and I'd have to hit Ctrl+Alt+Delete to "un-stick" it and continue to the Kubuntu shutdown screen process.  Thanks to UbuntuForums, I found the fix to that here:  [http://ubuntuforums.org/showthread.php?t=420999&page=2](http://ubuntuforums.org/showthread.php?t=420999&page=2) (which worked perfectly!). [B] Now, on to the next step.  First of all one thing I've noticed every since I installed the ATI Drivers with Envy:  at the Kubuntu login screen, it's displayed as "stretched" (for lack of a better term), almost as if it's expecting a wider screen or another screen altogether.  I can move my mouse to the right and it gets lost!  Then, when I login it kicks back to normal.  Why would it do this?  

My next question:  How can I set up a "Big Desktop" environment?  I use my laptop at work and have a big flat screen monitor on my desk that I'd like to use with it (like I did with Windows).  However I'd prefer it not to be mirrored, however two different screens (not stretched in tricking Kubuntu that it's one big screen), that I can use at the same time.  How can I go about doing this?  I've read I can do this with aticonfig and in the KControlCenter, but I don't want to mess anything up or what exactly the steps are.  Any help would be appreciated.  Thanks for the responses in advance![/B]

---

### Post by TMcKSmith on 2008-03-27
any help/resources would be greatly appreciated

---

### Post by NeoGreen on 2008-03-27
I never set up Dual Monitors in Ubuntu but I found this link that may be able to help you.  The only difference is that they are using a NVidia Card.  [http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/](http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/)

---

### Post by TMcKSmith on 2008-03-27
hmmm, thanks for the reply, but I'm pretty sure my issue is ATI-specific.  I say this only because I've tried quite a few different things already :)

---

### Post by NeoGreen on 2008-03-27
Try this link, I stumbled upon it [http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/](http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/)

---

