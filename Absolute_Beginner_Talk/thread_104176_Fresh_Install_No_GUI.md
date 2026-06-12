---
title: "Fresh Install: No GUI"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by MystaMax on 2005-12-15
Hello, I'm new here and very interested in this linux flavor.

I have installed ubuntu on the following configuration:

VMware 5.0 running on Windows 2k3 Server
Dell poweredge 2800 server (4 processors, 2GB of ram, 700 GB)

I gave the guest OS (in VMware) 10 gigabytes, disabled the sound and thats about it. mounted my dvd-install ISO, and began the install. I get all the way to where I have to config xserver-xorg, select the resolutions that I want enabled. After that it seems to copy some more files and then I get another error:

 [quote=Error from ubuntu install]  *Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?*[/quote] 

I then hunted through these forums and found [this thread]("http://ubuntuforums.org/showthread.php?t=98813&highlight=graphical+interface"). I took note of the tips from turtle.net, attempted the commands and got these messages:

> (EE) VMWARE(0): Driver can't support depth 24
(EE) Screen(s) found, but noe have a usable configuration

Fatel server error:
no screens found 
and then it continues w/ this:

> XI0: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

Not only do I want to resolve this, but I want to UNDERSTAND whats causing this.  I have screenshots of the errors I receive and will post if necessary. I'll say thanks advance to whoever and all who help out. Thanks! :razz:

---

### Post by kaamos on 2005-12-15
Can you log in the command line? If yes type:
```
sudo nano /etc/X11/xorg.conf
```
And find the line that says "DefaultDepth 24" and change it to "DefaultDepth 16". Exit with ctrl+x and save the changes.

The xserver is trying to use 24 bit colordepth which apparently is not supported in WMware.

---

### Post by TeeAhr1 on 2005-12-15
That you, Dave?

---

### Post by MystaMax on 2005-12-15
[quote=kaamos]Can you log in the command line? If yes type:
```
sudo nano /etc/X11/xorg.conf
``` And find the line that says "DefaultDepth 24" and change it to "DefaultDepth 16". Exit with ctrl+x and save the changes.

The xserver is trying to use 24 bit colordepth which apparently is not supported in WMware.[/quote] 
after looking over your post and bothering the linux gurus @ my job, I figured out my problem. It was a simple mistake, but we all do it:???:. Basically I have a server in our server room that we use for test and I was using remote desktop to adminster the session. Over RDP you can specify all display options like colors (8bit, 16bit, 24bit) and resolution. Normally I select only 8bit (which I guess Ubuntu doesn't support) to preserve network traffic (not that the other settings use alot). Anyway, I shutdown VMware restarted my Remote Desktop session @ a higher bit (16bit) and voila! it works. **Thanks for the help**, I really appreciate it. Now its on to setting up apache MySQL and PHP!

---

