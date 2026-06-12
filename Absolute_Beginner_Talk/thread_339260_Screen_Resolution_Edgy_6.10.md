---
title: "Screen Resolution Edgy 6.10"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-01-15
I have Edgy 6.10 up and running fr a few days now but I seem to be stuck with a 1280x1024 screen when I would prefer 1024x768.  I have tried to alter this in Screen Resolution but the screen goes black and eventually I am asked for my user name/password and it reboots back into 1280x1024.  Video card is ATI Rage Radeon X600 series. Any help appreciated.

---

### Post by riven0 on 2007-01-15
I'm guessing you haven't done a reconfiguration? That would be the first step. You can choose your resolutions from there. 
> 
sudo dpkg-reconfigure xserver-xorg

---

### Post by Quillz on 2007-01-15
You're using the Radeon x600. Have you installed and configured the fglrx driver?

---

### Post by bugster on 2007-01-15
Thanks both - er I don't know how to install/config the fgirx driver - sorry - very new to me.

---

### Post by bugster on 2007-01-15
> **riven0 said:**
> I'm guessing you haven't done a reconfiguration? That would be the first step. You can choose your resolutions from there.

I tried following this reconfiguration and think I screwed up.  The system rebooted and now runs in test mode and I think says the colours chosen was too high.  I've had to reboot in xp to get back here.  Guess I should have learned how to make a back up before I proceeded.  Any help greatly appreciated...:confused:

---

### Post by bugster on 2007-01-15
Sorry that should have read "in text mode "

---

### Post by bugster on 2007-01-15
Just thought - could I reboot from the edgy cd and edit the file "etc/x11/xorg.conf" to get back to where I was ?  Or maybe I'm clutching at straws ?

---

### Post by victorbrca on 2007-01-15
Hey Bugster,

  Don't worry. You probably just changed something in the configuration that you should not have. 

  I'd guess that reconfiguring the X-server (with the proper settings) once again would resolve. But wait for someone with more experience than me..... Sometimes it takes a while but someone is always there to help.

  Also when you reconfigure the X-server,  choose only the resolution that you want. And there's many ways of changing the resolution of your PC. Look as much as you can for a specific way for your card/PC.


Vic.

---

### Post by riven0 on 2007-01-15
Oh yeah, you can replace the xorg.conf from the LiveCD, but it's just easier to do a reconfiguration. When you get to text mode, just log in, and do **sudo dpkg-reconfigure xserver-xorg** again. Then choose what you think is the correct resolution and reboot again. Keep on doing this until you hit the right combination.

---

### Post by bugster on 2007-01-16
Thanks everyone - will try again this evening.

---

### Post by bugster on 2007-01-16
FIXED IT and got my desired screen resolution as a bonus.  Thanks everyone.

There will shortly be a question on here about how to make backups before reconfiguring things :oops:

---

### Post by riven0 on 2007-01-16
> **bugster said:**
> There will shortly be a question on here about how to make backups before reconfiguring things :oops:

:lol: If you do a reconfiguration, xserver should automatically backup your xorg.conf for you. To check your backups, you can either browse graphically through nautilus, or in the terminal:
> 
cd /etc/X11/ && ls -a

Your backup should look something like this, though the date may be different: xorg.conf20060116

---

