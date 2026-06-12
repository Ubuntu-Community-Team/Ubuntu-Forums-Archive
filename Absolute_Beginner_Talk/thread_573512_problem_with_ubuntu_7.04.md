---
title: "problem with ubuntu 7.04"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-11
hi,

In envy I can't download the NVIDIA driver. so how can i do it. And how to use the terminal in ubuntu? and Beryl on the other hand isn't running very well and i am also having trouble downloading compiz fusion. 

And I can't run the synaptic package manager, whenever i click on it a pop up shows up saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So how can I fix this??

Thnx

---

### Post by LowSky on 2007-10-11
> **limac said:**
> hi,

In envy I can't download the NVIDIA driver. so how can i do it. And how to use the terminal in ubuntu? and Beryl on the other hand isn't running very well and i am also having trouble downloading compiz fusion. 

And I can't run the synaptic package manager, whenever i click on it a pop up shows up saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So how can I fix this??

Thnx

run this command in the terminal
```
sudo dpkg --configure -a
```

the run
```
sudo apt-get update
```

---

### Post by aktiwers on 2007-10-11
Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1

Log in.
type:
```
sudo /etc/init.d/gdm stop
```
```
cd Desktop
```And then 
```
sudo ./Nvidia-Linux-x86-100.14.09-pk1.run
```when done.. type:
```
sudo reboot
```
For your other problem, did you try to run the command suggested?

```
sudo dpkg --configure -a
```

---

### Post by limac on 2007-10-11
hey low sky and aktiwers,

thanks a lot for ur help man. Thanks a lot. My lixux is as good as new. By the way how come u guys come to know about these code. Can u pls reveal that secret to me??

Thnx a lot by the way....

---

### Post by aktiwers on 2007-10-12
No problem limac.

You learn by asking and helping people here on the forums :)
Google search for "howto ubuntu <insertwhateverhere>" is good too..

---

