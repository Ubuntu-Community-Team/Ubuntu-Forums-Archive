---
title: "Virtualbox VM won't start after kernel upgrade"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by onero on 2007-05-29
I posted this in the virtualbox forums as well, but I'm posting this here as well in case someone can help (because I really need my windows VM @_@)

Am using Feisty 7.04, and previously I was using a Windows XP guest on Virtualbox with no problems. Today, the update notifier informed me that there were updates to the kernel, so I went ahead and updated. I was previously using the low-latency 2.6.20.15 kernel, and when I upgraded and rebooted, I used the low-latency 2.6.20.16 kernel. I logged into Ubuntu and everything was fine, but when I started my Windows XP VM, I got an error saying:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


I tried to run /etc/init.d/vboxdrv setup, but when I did, I got this error in vbox-install.log:

Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.. Stop.


Any idea what I should do? I don't know where to specify the kernel directory, and even if I did I wouldn't know what directory to put.

BTW, I already tried reinstalling, but it gives the same error. I've also rebooted twice already. Thanks!

---

### Post by AndyCooll on 2007-05-29
Yeah, you'll need to reinstall it. You have to do this whenever the kernel is updated (you have to do this with VMware too).

:cool:

---

### Post by Bachstelze on 2007-05-29
You must install the kernel headers matching the new kernel :

```
sudo apt-get install linux-headers-$(uname -r)
```

Then just run 

```
sudo /etc/init.d/vboxdrv setup
```

and you should be fine. No need to reinstall anything.

---

### Post by onero on 2007-05-29
Yay, thanks! That worked after I rebooted.

---

### Post by Bachstelze on 2007-05-29
There was no need to reboot either ;)

---

### Post by Sethalos on 2007-05-31
Hiya, 

I tried the above commands, and this didn't work for me, after running the commands here is what I saw:

Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sethalos@sethalos-linux:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

I rebooted, and tried to start up VB and recieved the error:


VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I've tried Uninstalling and reinstalling as well, no joy.

Seth

---

### Post by Sethalos on 2007-06-01
Ok, for some reason I had to do it twice, it works fine now.

---

### Post by Unicast on 2007-06-03
> **HymnToLife said:**
> You must install the kernel headers matching the new kernel :

```
sudo apt-get install linux-headers-$(uname -r)
```

Then just run 

```
sudo /etc/init.d/vboxdrv setup
```

and you should be fine. No need to reinstall anything.

Whoot! :popcorn:

Just run into this problem myself. Thanks a million!

---

### Post by isecore on 2007-06-05
> **Sethalos said:**
> Hiya, 

I tried the above commands, and this didn't work for me, after running the commands here is what I saw:

Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sethalos@sethalos-linux:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

I rebooted, and tried to start up VB and recieved the error:


VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I've tried Uninstalling and reinstalling as well, no joy.

Seth

The solution to your problem is right there in front of your nose :)

Ahem. How about this? <b>"Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect."</b>

---

### Post by lazyart on 2007-06-05
> **isecore said:**
> The solution to your problem is right there in front of your nose :)

Ahem. How about this? <b>"Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect."</b>

Ahem. How about this? > Ok, for some reason I had to do it twice, it works fine now.
User found the solution.

Play nicely now. :)

---

### Post by softbomb on 2007-10-19
Just for the record I had this same problem after upgrading to 7.10. The solution posted worked for me too. Cheers!

---

### Post by myoungf1 on 2007-11-10
> **HymnToLife said:**
> You must install the kernel headers matching the new kernel :

```
sudo apt-get install linux-headers-$(uname -r)
```

Then just run 

```
sudo /etc/init.d/vboxdrv setup
```

and you should be fine. No need to reinstall anything.

Thanks for this information.  I thought my vbox windows xp was gone after the upgrade from feisty to gutsy, but this worked wonderfully.  And yes you don't need to reboot to get this working just restart virtualbox and everything will be fine.

---

### Post by carusoswi on 2007-12-08
This posted solution worked for me, also, but I am left with this unanswered question:

I was toying around with the settings of my VB XP machine, checking to see if I could gain access from the machine to the hard drives and folders on my dual boot xp/linux machine, and was not connected to the internet at the time, nor had I updated the kernel or anything like that when VB stopped working.

Without internet connection, I could not sign on here to look for the solution.

My question is:  what "broke" my VB?  I would think it impossible to set some switch in the settings dialog box that could break the machine which could not simply be reversed to restore proper operation.  As I mentioned, I was not connected to the net at the time, so there was no possibility that I updated something by accident . . . so what do you think caused my problem?

Thanks.

Caruso

---

### Post by podness on 2008-05-19
> **Sethalos said:**
> Hiya, 

I tried the above commands, and this didn't work for me, after running the commands here is what I saw:

Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sethalos@sethalos-linux:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

I rebooted, and tried to start up VB and recieved the error:


VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I've tried Uninstalling and reinstalling as well, no joy.

Seth

Now with the new Kernel (That's of Ubuntu 8.04) - I installed the latest Linux Mint 5 Elyssa (based on Ubuntu). This is the same error I get when I try to launch Windows XP machine (so I can install the XP OS over VirtualBox).

Now I checked a few good times, I'm the only user on this machine so there are no mistakes. I AM in the "vboxusers" users group. I tried to log out, I tried to reboot.. nothing helped it. The error is still there. I also tried to reinstall VB a few times.

I tried out what worked for Seth, the command > sudo /etc/init.d/vboxdrv setup" did not work as "setup" is no longer an available parameter. I can only do the next "sudo /etc/init.d/vboxdrv (start|stop|restart|status)"

I tried stopping and starting or just restarting again and again after of course running the next command first "sudo apt-get install linux-headers-$(uname -r)". I tried adding the Kernel version for VB using the Package Manager. The new kernel version seem to work but it just doesn't give me permission..

> "

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
"

Help would be very well appreciated

Edit:
Just in case, I have a validation that I am grouped in the right place.
using:  > cat /etc/group  at the end of the list I get this: > vboxusers:x:126:my_username_here_spelled_correctly

and again.. I tried to log out and I even rebooted but nothing helped..
I also checked the permission of the folder>  /dev/vboxdrv  and the settings for group permissions seems to be correct:

> crw-rw---- 1 root vboxusers 10, 63 2008-05-19 14:17 vboxdrv

---

### Post by podness on 2008-05-20
Well I changed back to windows for a while.. then I logged my Linux again. Somehow by mistake I removed my admin status so I rebooted to recovery mode and used nano to edit /etc/group 

Then after I added myself to sudo and admin group, I logged in back. Sudo was working again, just for the kicks.. I tried launching VirtualBox again and it worked with no problem. Then of course I got my admin setting back online.

It just decided to work, I'm not sure why. Could be because I made some manual changes in the /etc/group .. I added myself to my own group as well (your own group: that which is named after your user name). Something in those two actions did the trick. I hope it could help anyway else having anything similar to this problem I had.

---

