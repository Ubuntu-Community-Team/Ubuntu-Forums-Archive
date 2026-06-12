---
title: "Login screen only displays spinning cursor just prior to login screen"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by heatpumpcontrol on 2007-04-28
Hello and thanks to you all for all the input on these forums.

I've been playing with Ubuntu now for 10 days and of course it's break and install, break and install. Anyway, I've had this problem before but have not found a solution on google or the forums.

Everything will be fine until a reboot. But, after what appears to be a good boot up, my screen displays normally upto the point just before the login name graphical display shows up. All I have is a rotating cursor that never stops. I've tried messing with the 'x' something config file but nothing. 

I have noticed that this only happens on my desktop. I am currently using my laptop with Ubuntu installed on it too but it has not given me this problem. The difference between the two is that on my desktop, I have a 'Restricted NVidia Driver' activated for 'Desktop Effects'. I believe this may be the problem. It happened this time after installing FF plugin for Java...JRE. 

The laptop has 'Desktop Effects' turned on also but it is using its own display drivers.

I have had to install the O/S three times now because of this but it isn't untill now that I've come to a conclusion that it might be 'Desktop Effects' causing the problem. 

How can I get back into the login screen without reinstalling the O/S? IE: deactivate 'Desktop Effects' or using another graphical interface.

I have a /home partition and after a re-install and saving /home, my screen came up but this time it went all white. I couldn't see the cursor. I'm reinstalling again and I've formatted my /home. Fortunately I don't have anything there. 

I have seen other posts similar but not exactly like this. So any help would be appreciated.


I found a way to repair. I believe it had to do with 'Desktop Effects'. After the reinstall though I left it disable but I found out how to restore my 'xorg.conf' file and/or manipulate it.

Here's the link.
[http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver]("http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver")

---

### Post by bjornhakon on 2007-05-21
I have the same problem. It started after I changed the login screen (just another style, really) and activated both automatic login and timed login (to make the given user log in automaticly after 30 sec.).
The result was exactly what you describe.
By the way, I run Ubuntu 7.04 with Gnome.

---

### Post by heatpumpcontrol on 2007-05-22
> **bjornhakon said:**
> I have the same problem. It started after I changed the login screen (just another style, really) and activated both automatic login and timed login (to make the given user log in automaticly after 30 sec.).
The result was exactly what you describe.
By the way, I run Ubuntu 7.04 with Gnome.

Well to be honest with you I never did figure it out. I ended up reinstalling the O/S. However, I believe that if you do look for help on xserver in cntl+alt+f1 mode using nano ie: sudo nano /etc/X11/xorg.conf. Some forums will help you with the configuration of your xserver to restore it.

good luck
HPC

---

### Post by heatpumpcontrol on 2007-06-25
Never mind. We'll figure this out ourselves. When I become savvy in Linux, I'll come back and post a fix for future beginners. I'm sure this has happened and continues to happen to others. I've tried Xubuntu and the same thing happened after an update. I reinstalled the O/S on that too. 

Thanks.

---

### Post by carlmccall on 2007-08-14
Since I changed to auto login of my non-admin account there is no way to login as admin. Logging out to switch users freezes my computer.

Is there a way to force the login panel to reappear so I can login as admin again or am I going to be forced to ditch Ubuntu as unusable and tell people NOT to use it?

So far I've been telling people to switch from Windows to Ubuntu. Until I tried installing Ubuntu on the second internal hard drive and made one mistake and it's unusable now.

I'll just tell people Ubuntu isn't usable yet: I've been in computing 30 years and no one can tell me how to 'do something simple' like disable automatic login for a non-admin user while logged in as that user.

---

