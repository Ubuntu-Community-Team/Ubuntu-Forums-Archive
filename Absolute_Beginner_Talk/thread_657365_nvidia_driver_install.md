---
title: "nvidia driver install"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by kalkabun on 2008-01-03
hi...very newbie here...any help appreciated with thanks

trying to install NVIDIA_Linux-x86-1.0-9755-pkg1.run from 
LXFDVD100 on Ubuntu 7.10 via paste into terminal in root 
with 'sh' command...I get the message 

'You appear to be running an X server; please exit X before             
installing.  For further details, please see the section INSTALLING   
THE NVIDIA DRIVER in the README available on the Linux driver         
download page at [www.nvidia.com](www.nvidia.com).'

...I tried  --no-x-check
not sure if this has worked 'or is advisable' nevertheless
when I try to alter visual effects I get the message 

'The software source 
for the package
nvidia-glx-new
is not enabled.'

the PC is not connected to the internet, but would nevertheless 
like to learn to do it this way/the right way/the nice way :O)
:)

---

### Post by ~LoKe on 2008-01-03
Press ctrl+alt+f1, then log in.  Once you've logged in, cd to the directory with the driver then:
```
sudo /etc/init.d/gdm stop
```
```
sudo sh NVIDIA*.run
```
```
sudo /etc/init.d/gdm restart
```

---

### Post by FreakTech on 2008-01-03
If you are running 7.10 you could use the restricted driver manager

---

### Post by Daveth on 2008-01-03
are you aware of this?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by nachomania on 2008-01-03
Check your card first! I just messed up my linux box (5 minutes) installing an nvidia driver. Make sure!

---

