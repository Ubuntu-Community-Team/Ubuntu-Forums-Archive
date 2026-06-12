---
title: "Resolution problems using VNC Viewer (Remote Desktop on Ubuntu)"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by steven_mckenz on 2007-01-17
I have Remote Desktop enabled on my Ubuntu Server.  I have VNC Viewer that I have been using to connect to the server in order to do stuff on it, as both my Windows system and the Linux Server are on the same network.  I haven't had any issues connecting to it or using VNC to control the system.

However, after finally getting the new system and network all set up, I don't have a monitor connected to the Linux system.  My main objective was to only have it connected to the network with a simple CAT5 cable, and when I wanted to use it, I would just use VNC Viewer from one of my Windows machines to control and use it.  This seemed to work just fine, and it was running at 1280x1024 resolution (which is my monitor's resolution).

I then had to reboot the Linux machine, and when it came back up (with no monitor attached) and I used VNC to view/control it, it was at a resolution of 640x480.  Obvioulsy this resolution is AMAZINGLY small.  And when I try to go to the resolution preferences, it doesn't even give me the option to select the other resolutions, such as 1280x1024, which I would like to use, and was using right before a system restart.  The xorg.conf file is fine, as it was working perfectly fine before the restart.  Only after the restart, which was the first time restarting it w/o a monitor attached, did it decide to pick the resolution of 640x480, and not let me resize it to a better resolution.

Is there some way that I can force it to have the resolution of 1280x1024, and not need to have a monitor attached to it?  Thanks!

---

### Post by steven_mckenz on 2007-01-17
Anyone?

---

### Post by steven_mckenz on 2007-01-17
Can someone give me any ideas?  I was hoping that this issue wasn't TOO hard to fix, but now I'm getting a little worried......!  ](*,)

---

### Post by steven_mckenz on 2007-01-17
Well, I got the problem fixed.  Either it was a really difficult issue and nobody knew the solution to it, or it was a simple problem that has been asked too many times.  If that's the case, I'm sorry for making a new thread.

But to solve the problem, I added a horizontal sync and vertical refresh variable in the xorg.conf file, which then forced the system to activate all available resolutions, and then by default set me at the largest resolution, which was 1280x1024, which was what I was wanting.  :D

---

### Post by vjones777 on 2007-02-11
Thanks for posting that - thats useful.

---

### Post by stewacide on 2007-06-11
Thanks a lot, adding the h and r sync to the xorg.conf did it :D

---

