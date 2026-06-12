---
title: "changed video driver, now cant start gui"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wcampbell on 2007-04-06
Hi,

I was trying to get the "desktop effects" working in Feisty and changed my video driver from "nvidia-glx-legacy" to "nvidia-glx".  After reboot, I learned the hard way that my video card must be older than I thought it was.  

How can I revert to the older driver from the command line I boot to?

(FYI, boots to "Failed to start the X-server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?.... and all that stuff is greek to me.

Thanks in advance,
Warren

---

### Post by overdrank on 2007-04-06
> **wcampbell said:**
> Hi,

I was trying to get the "desktop effects" working in Feisty and changed my video driver from "nvidia-glx-legacy" to "nvidia-glx".  After reboot, I learned the hard way that my video card must be older than I thought it was.  

How can I revert to the older driver from the command line I boot to?

(FYI, boots to "Failed to start the X-server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?.... and all that stuff is greek to me.

Thanks in advance,
Warren

Hi its ok I have done that many of times. At the end of the review of the xorg you will get a prompt for your login. Login and then enter the command sudo dpkg-reconfigure xserver-xorg and then answer the questions and then you will be back to the regular screen, Then you can reinstall your drivers. Good luck and welcome!:)

---

### Post by nudnik on 2007-04-06
> **wcampbell said:**
> Hi,

I was trying to get the "desktop effects" working in Feisty and changed my video driver from "nvidia-glx-legacy" to "nvidia-glx".  After reboot, I learned the hard way that my video card must be older than I thought it was.  

How can I revert to the older driver from the command line I boot to?

(FYI, boots to "Failed to start the X-server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?.... and all that stuff is greek to me.

Thanks in advance,
Warren

I would log into root from the command line (sudo -s and then your password). Then type the following:

sudo /etc/init.d/gdm stop
sudo aptitude remove nvidia-glx
sudo apt-get install nvidia-glx-legacy
sudo nvidia-xconfig

If the above operations are performed successfully, then type:

reboot

That should be shorter and easier than reconfiguring the xserver.

If you need to reconfigure the xserver in future for whatever and lack expert knowledge, type:

sudo dpkg-reconfigure -phigh xserver-xorg

That will do most of the work for you, other than choosing a resolution.

---

### Post by wcampbell on 2007-04-06
thanks again.... might repost if I cant figure out what answers will get me going again....

also, I gotta mention how impressed I am with the average time that it takes for someone to respond to a support post.... cant wait to know enough to return the favor.

---

### Post by Razorback on 2007-04-06
You should be able to Ctrl-Alt-F1 where you get the X server failure and go to a command line.  Then, use sudo dpkg-reconfigure xserver-xorg to change your driver.

You can also do a "sudo nano /etc/X11/xorg.conf" to text edit your driver back to where it was.

I have crashed X before experimenting.  Great thing is it is really hard to bork the system. :)

---

### Post by wcampbell on 2007-04-06
yeah, I'm not sure that I have the knowledge needed to reconfigure using the first solution... seems like whatever I choose give the same result....

I tried the first part of nudnik's recommendation, but I got "unknown command" or something like that with "sudo nvidia-xconfig"....

in the end,  sudo dpkg-reconfigure -phigh xserver-xorg did the trick.

---

### Post by jbumgar on 2007-04-06
type sudo dpkg-reconfigure-phigh-xserver-xorg

Then choose vesa.  

Then i believe you reboot and you should be back to the desktop.  Then using Envy you should be back in business in no time.

---

### Post by nudnik on 2007-04-06
> **wcampbell said:**
> yeah, I'm not sure that I have the knowledge needed to reconfigure using the first solution... seems like whatever I choose give the same result....

I tried the first part of nudnik's recommendation, but I got "unknown command" or something like that with "sudo nvidia-xconfig"....

in the end,  sudo dpkg-reconfigure -phigh xserver-xorg did the trick.

Well, I am glad at least a part of it was useful to you. Unknown Command: I probably remember the command incorrectly....its bad to get old.

---

