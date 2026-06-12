---
title: "Remote Desktop Resolution"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by snidely on 2007-07-25
Hi

I'm trying to configure remote desktop and by default I'm getting a resolution of 640 x 480.

I've seen from other posts that if you add vertical and horizontal refresh rates to the /etc/X11/xorg.conf file this fixes the problem.

However, I'm not sure what lines I need to add or where abouts in the file I need to add them. Any advice?

Thanks.

---

### Post by l3f3vr3 on 2007-07-25
Remote Desktop to windows or to Linux?  From what I have done the remote desktop to linux uses VNC with the display as :0 so if the computer is already running higher resolution it should mimic that.  Windows remote desktop uses rdesktop as a client or even tsclient.  
Tsclient has a gui to change the resolution and from the command line rdesktop uses a -g 1600x1400 for the resolution.

---

### Post by phr0ze on 2007-07-25
Sometimes when you run a remote desktop it runs at reduced color. Your resolutions defined for the lesser bit depths may not be as defined as the 24bit depth. I wouldn't change the sync rates at all for this type of problem. The sync rates should only matter to a monitor connected directly to the box and you want the proper rates to prevent damage to the monitor.

---

### Post by snidely on 2007-07-26
Hi

I've enable remote desktop in ubuntu and am using tightvnc on my WinXP machine. 

If I directly connect to the ubuntu pc (i.e. attach a monitor), I get a resolution of 12xx X 10xx

However, when I disconnect the cable and leave the ubuntu box headless and use tightvnc to log into it I get a resolution of 640 X 480.

I'm not really sure how to fix it! Any suggestions?

Thanks.

---

### Post by effinboy on 2007-09-30
I too have the same issue, I'm doing  my best to learn ssh, but there are somethings I'd prefer to use tightVNC on windows for. It works great all but the resolution, 800x600. I'm using the default "Remote Desktop" built into 7.04. Any help on how to get it to a higher res would be awesome. Thanks in advance!

---

