---
title: "x-server failed"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by timo_01 on 2007-06-21
hi to you all

when i boot my computer,i get the following "failed to start the x-server(your graphical interface).it's likely that it's not set setup correctly.would you like to view the xserver output to diagnose this problem?" yes...
nvidia (0) failed to load the nvidai kernel module.... 
and directly goes to the command prompt

i had earlier install using ```
sudo apt-get install nvidia-glx
``` and later did ```
sudo apt-get install nvidia-glx-new 
``` but this does not solve the above problem.

i have the latest kernel  2.6.21.5, nvidia geforce GO 6100

please how can i fix this?
thank you

---

### Post by Jimmyfj on 2007-06-21
sudo dpkg-reconfigure xserver-xorg

---

### Post by atria on 2007-06-21
I think you need to reconfigure your xserver. Execute

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure it

---

### Post by dannyboy79 on 2007-06-21
that's not going to do it, you're having conflicting modules problems. I bet if you view the error log right after your x server fails to load, it says something like, trying to load nvidia module 9755 but nvidia kernel is 9736 or something similar. Also, most likely it says somethign about API mismatch. 

This is because you didn't properly remove and purge the nvidia-glx driver before you installed the first one. Also, if you do in fact need the nvidia-glx-new (Nvidia driver 9755) then you need to add "nv" to the /etc/defaults/linux-restricted-module file in order for the machine NOT to try to load hte incorrect module.

first try to remove and purge everything related to nvidia-glx*

sudo aptitude remove nvidia-glx* && sudo aptitude purge nvidia-glx*

then do 

sudo dpkg-reconfigure xserver-xorg
and chose the vesa driver temporarily, chose all defaults for anything you don't know the answer to, make sure you hit the space bar on any resolutions that you know your card supports. then restart your (ctrl-alt-backspace) x-server which will use the vesa driver temp. then do 

sudo aptitude install nvidia-glx-new

then change your driver to "nvidia" in your xorg.conf. then make sure you edited the linux-restricted-modules file like I said above, then restart your x server again and that should be it. if it doesn't work, still log into the command line, then do this command

dmesg

and towards then end of that output, you'll see something about the nvidia module tainting the kernel and it'll say which module it tried to load, it should be 9755 and if it's not, then you either didn't purge and remove or you didn't update that file I informed you to update. Good Luck

---

### Post by timo_01 on 2007-06-21
> **dannyboy79 said:**
> that's not going to do it, you're having conflicting modules problems. I bet if you view the error log right after your x server fails to load, it says something like, trying to load nvidia module 9755 but nvidia kernel is 9736 or something similar. Also, most likely it says somethign about API mismatch. 

This is because you didn't properly remove and purge the nvidia-glx driver before you installed the first one. Also, if you do in fact need the nvidia-glx-new (Nvidia driver 9755) then you need to add "nv" to the /etc/defaults/linux-restricted-module file in order for the machine NOT to try to load hte incorrect module.

first try to remove and purge everything related to nvidia-glx*

sudo aptitude remove nvidia-glx* && sudo aptitude purge nvidia-glx*

then do 

sudo dpkg-reconfigure xserver-xorg
and chose the vesa driver temporarily, chose all defaults for anything you don't know the answer to, make sure you hit the space bar on any resolutions that you know your card supports. then restart your (ctrl-alt-backspace) x-server which will use the vesa driver temp. then do 

sudo aptitude install nvidia-glx-new

then change your driver to "nvidia" in your xorg.conf. then make sure you edited the linux-restricted-modules file like I said above, then restart your x server again and that should be it. if it doesn't work, still log into the command line, then do this command

dmesg

and towards then end of that output, you'll see something about the nvidia module tainting the kernel and it'll say which module it tried to load, it should be 9755 and if it's not, then you either didn't purge and remove or you didn't update that file I informed you to update. Good Luck

this worked but found that (according to me) this was related with the latest kernel(2.6.21.5) (not opening linux-restricted-modules-common via "system-admin-restricted driver manager") because with the default one,no problems.
**note:**it should be 
```
/etc/default/linux-restricted-modules
``` 
not
 ```
/etc/defaults/linux-restricted-module
```

thank you all for your replies

---

### Post by dannyboy79 on 2007-06-21
> **timo_01 said:**
> this worked but found that (according to me) this was related with the latest kernel(2.6.21.5) (not opening linux-restricted-modules-common via "system-admin-restricted driver manager") because with the default one,no problems.
**note:**it should be 
```
/etc/default/linux-restricted-modules
``` 
not
 ```
/etc/defaults/linux-restricted-module
```

thank you all for your replies

thanks for clarifying, use tab completion, it saves you time!

---

