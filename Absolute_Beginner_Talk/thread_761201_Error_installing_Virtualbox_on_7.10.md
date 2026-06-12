---
title: "Error installing Virtualbox on 7.10"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by boysha on 2008-04-21
I get this error when I try to install Virtualbox using Add/Remove Applications...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone help me? 

Thanks!

---

### Post by mgranet on 2008-04-21
Did you try running dkpg  --configure -a in the terminal? What was the result?

---

### Post by boysha on 2008-04-21
I tried but it wouldn't do it - saying something about administrative rights although I
am an administrator...or maybe I am doing something wrong...In any case it wouldn't
let me do it. I am however very new to Linux so...Any help is greatly appreciated.

---

### Post by bumanie on 2008-04-21
> sudo dkpg --configure -a in terminal will correct the problem. This occurs if there has been an interruption to the download for some reason. It will recommence from where it was up to before the interruption.

---

### Post by boysha on 2008-04-21
Are you saying that I should try it again and it should pick up where it stopped the last time?

---

### Post by bumanie on 2008-04-21
No. Put sudo in front of the command you first used, that gives you the 'root privileges' it said you were missing. Copy and paste the command I posted - it should work.  and the download will begin where it left off, You should not have to do anymore until it is finished.

---

### Post by boysha on 2008-04-21
Thank you! I will try that when I get home (after work) and let you know.
All the best,
Neb

---

### Post by boysha on 2008-04-21
I did what you said and I did install Virtualbox.
I wanted to install Windows XP (so I can run AutoCAD) but this is the message I got and I really don't know where from here...Help, please...


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by akiratheoni on 2008-04-21
> **boysha said:**
> I did what you said and I did install Virtualbox.
I wanted to install Windows XP (so I can run AutoCAD) but this is the message I got and I really don't know where from here...Help, please...


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

When you install VirtualBox, you also need to add your user to the vbox user group.  I did it a different way but maybe this one will work:

```
sudo adduser yourusername vboxusers
```

You'll need to log out and log back in.

---

### Post by boomdiddly on 2008-04-21
ok first check that your username is ticked in the vboxusers group. You can check this by going:

System > Administration > Users and groups

Then click Manage Groups, scroll to vboxusers, click properties and that will show you who is in there. when ticked restart gnome by pressing Ctrl+Alt+Backspace and try it then, you may need to restart to complete system but i can't remember.

Paul

---

### Post by boysha on 2008-04-21
Thank you! That worked great...I am installing Windows XP...
Regards,
Neb

---

### Post by moma on 2008-04-23
Please take a look at this guide, section C):**[http://www.futuredesktop.org/vmware/vmware-player-gutsy.html](http://www.futuredesktop.org/vmware/vmware-player-gutsy.html)** (for Ubuntu 7.10 )
.
.

---

