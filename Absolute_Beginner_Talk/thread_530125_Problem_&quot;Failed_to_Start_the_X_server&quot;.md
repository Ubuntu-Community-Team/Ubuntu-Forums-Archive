---
title: "Problem: &quot;Failed to Start the X server&quot;"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by elang1003 on 2007-08-20
i am a beginner of Ubuntu. several days ago,  after my  friend helped me to update my graph card ( NVIDIA GeForce 8800 GTS) and restarted the computer, an error message:" Failed to Start the X server" appeared on the screen.
i tried using "$ sudo dpkg-reconfigure xserver-xorg" to fix it but failed.
please help me, thank you in advance.

some information list as follow:
ww: /usr/share/fonts/x11/cyrilic does not exist 
ww: counld not open module "wfb" 
ee: NVIDIA(0): Need libwfb but wfb screenInit not found 
Fatal server error: add screen (screenInit failed for drive 0)

my ubuntu release 7.04

---

### Post by heimo on 2007-08-20
To get it at least working, reconfigure again, but select nv or vesa driver instead of nvidia.

---

### Post by elang1003 on 2007-08-20
Hi, heimo, thank you for your answer. I've tried  this means last night. I failed to get rid of this problem. And another question appears (I think it is even worse). Now, I cant log in the system. Whatever I input after the cursor, there is no response.
ohh?

---

### Post by heimo on 2007-08-21
> **elang1003 said:**
> Hi, heimo, thank you for your answer. I've tried  this means last night. I failed to get rid of this problem. And another question appears (I think it is even worse). Now, I cant log in the system. Whatever I input after the cursor, there is no response.
ohh?

Are you saying keyboard doesn't seem to work at all, or that entering any command doesn't give any output at all? Can you log in to your system on virtual console? No? I can't see connection between changing xorg.conf and command line not working, that just doesn't make any sense.

---

