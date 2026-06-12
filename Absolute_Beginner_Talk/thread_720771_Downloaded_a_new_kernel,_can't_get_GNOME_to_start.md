---
title: "Downloaded a new kernel, can't get GNOME to start"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by seagullplayer77 on 2008-03-10
A friend of mine came over to try to solve a previous problem (which isn't important AT ALL to me right now), and he downloaded the generic 2.6.22-14 kernel image, along with a few other 2.6.22-14-generic kernel packages, from Synaptic. When he rebooted, my realtime kernel (I'm using Ubuntu Studio) came up, and so did the generic kernel. When I tried booting into the realtime kernel, I got a big error message--literally big--as in the letters were too big to read the whole message--and I couldn't get to my desktop. I can log in just fine from the login screen, but after that it all goes downhill. I tried booting the generic kernel, and I got the same story there.

I tried booting Knoppix from the Live CD, but I couldn't really find anything that seemed out of the ordinary--other than all of the generic kernel stuff in the /boot folder. My friend (who I'm not too happy with right now) thinks that it's an xwindows problem, but he also thought downloading the generic kernel would be a good idea. Grrr...

I didn't really have anything important on my Linux partition, so if I have to do a reinstall, I guess that's what I have to do. I'd really like to avoid it, though. I've got a lot of stuff to do, and I'd like to avoid reinstalling an operating system and customizing it again if I can at all avoid it.

---

### Post by dokdoom on 2008-03-10
Honestly if I were you I would reinstall. It sounds like X is broken and while I can't imagine a kernel altering your xorg.conf something is definatley wrong. (Like I needed to tell you that right :) ..) If you are familiar with exiting your xorg.conf file I could walk you through some steps to make sure nothing did change. But for now if you want to see what's happening do the following.

Try and start your computer even though it won't work this is fine, we want to generate some logs. Since your resolution is all messed up manuvering through the gui is out of the question hit CTRL + ALT and F1. You should be at a terminal window now, if you are not used to the command line don't worry this will be quick and painless. Important note is you are doing this after a failed attempt of logging on. 

From your terminal, login using your normal crednetials and type ls -ltr /var/log. This will show you a list of all of your logs, note: the ones nearest the bottom are most recent. Now with that list in front of you lies all of the information you need to google to resolve this issue or at least provide someone here with some logs to look at. Say the last log on the list is Xorg.0.log. From your prompt type 

tail /var/log/Xorg.0.log and assuming this is a problem with X you should see some relative errors. The errors are also time stamped so if you see an error from earlier today or yesterday (unlikely) you know it doesn't pertain to your problem. 

In your log you just tailed should be some lines with II or EE or WW, look for the EE lines and do a google search to see what other users have done to fix said problem.

Like I said, I would just reinstall but I also wouldn't let me friends install kernels on my OS either. Don't feel bad, lesson learned but once you find your logs you should have a better idea of where to go and what to do.

I hope this helps you with your problem(s).

---

### Post by neurostu on 2008-03-10
Sounds like you screwed your kernel... Honestly it will take you 35 minutes to reinstall ubuntu. It will take you 2-3 + hours to fix the kernel

Granted you will probably learn a lot if you chose the harder route, but if i were you I would just reinstall!

---

### Post by forrestcupp on 2008-03-10
It sounds like you have proprietary video card drivers that got broken when you updated the kernel.  What video card do you have?  You can boot to the recovery console and type:
```
dpkg-reconfigure xserver-xorg
```
Add a sudo to the front of that if you're not root.  When you are manually reconfiguring X, choose the vesa drivers.

Then you should be able to boot to your desktop and reinstall your proprietary drivers for your video card.  If the drivers in the Restricted Drivers Manager don't work for you, try [Envy](http://albertomilone.com/nvidia_scripts1.html) if you have nvidia or ATI.

---

