---
title: "Installing nVidia drivers ... Please help!!!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by jamesb2007 on 2007-05-01
I am obveously new at this.. I have a nvidia geforce 6800GS and I have enabled the driver for it but my resolutions are way way off... the best I can get is 1024x768 at 54Hz ... I want to run at 1280x1024 @ 75Hz... how can I do this?? I have downloaded a file from nvidia.com called NVIDIA-Linux-x86-1.0-9755-pkg1.run   what do I do with this??? it's on my desktop so if I need to do a command or something... please help!!

---

### Post by bodhi.zazen on 2007-05-01
Try envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From the terminal :

```
mkdir -p ~/src/envy
cd ~/src/envy
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu5_all.deb
sudo dpkg -i envy*
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

Yes, I know sudo dpkg -i envy is in there twice ...

Then, in a terminal, type ```
envy -t
```

Select install nvidia driver :)

restart X ~ log out, at the log in screen type Ctrl-Als-Backspace

			Then, in a terminal : ```
gksudo nvidia-settings
```
				Set up your monitors for twinview, set the resolutions, ect, then click the "save 							settings" button.

---

### Post by jamesb2007 on 2007-05-01
Ok.. everything is fine until I get to the part after "Select Install nvidia driver" it asks if I want to automatically configure my xorg.conf and I put "Y" and then it asked if I wanted to start or restart the Xserver... Default said "Y" so I said "Y" and went to a black screen with some text, what do I do from there??????

---

### Post by bodhi.zazen on 2007-05-01
> **jamesb2007 said:**
> Ok.. everything is fine until I get to the part after "Select Install nvidia driver" it asks if I want to automatically configure my xorg.conf and I put "Y" and then it asked if I wanted to start or restart the Xserver... Default said "Y" so I said "Y" and went to a black screen with some text, what do I do from there??????

did you get an error message ?

If not, restart gdm (gdm = login screen)

```
sudo /etc/init.d/gdm restart
```

---

### Post by jamesb2007 on 2007-05-01
Ok.. all is installed and I'm using my resolution of 1280x1024... now when you told me to set up my monitor as twinview.. I can't, it's grayed out. Also.. when I try to change the refresh to 75Hz like I should be able to ... I get a message saying to use what works or something... What's going on with that? Why can't I use 75Hz?

---

### Post by jamesb2007 on 2007-05-01
NEVER MIND!! It's working now!! THANKS A MILLION BUDDY!!!!!!!!!!!!!!!!!!!!!:guitar:

---

