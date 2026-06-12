---
title: "Install nVidia 5900 ultra. Help needed!"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by jjbennee on 2005-09-07
I downloaded the latest nVidia driver for my nVidia 5900 ultra and when I ran the program it told me that I need to be in root.  So I figured out how to log into root (which is System -> Administration -> Login Screen Setup.  Then you need to enter the root password.  Under the Login Screen Setup, there is the "Security" tab and make sure the "Allow root to login with GDM" is checked.  Then you can log out and log back in again with root as the user name)  I then ran the driver again from the terminal (#**sh NVIDIA-Linux-x86-1.0-7676-pkg1.run** ) and got this error
-----------------------------------------------------------------------------------------------------------------------------------
 ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

                                       OK
-----------------------------------------------------------------------------------------------------------------------------------
So how do I run this program out of the Unbuntu X server?  I read the README and it said boot the computer in terminal only.  How do I do that in Unbuntu?  I booted the computer and there is no option to boot into just the terminal.  Can someone help me?  

P.S. (I also just found out that I can type "$su root" to get into root as well and didn't have to go through that long process listed above)

---

### Post by ltmon on 2005-09-07
Hi,

First up, unless you need the absolute latest drivers (I'm not familiar with what card needs what drivers) the easy way is to follow:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

If you do need the latest, greatest drivers read on:

THere are many ways to do this... but mine is:

1. Start up as normal
2. Ctrl-alt-F1 (this brings up the terminal)
3. Login as normal
4. Type:

sudo /etc/init.d/gdm stop

This will stop the graphical environment (which is still running in the background before you do this).

5. Type

sudo sh NVIDIA-Linux-x86-1.0-7676-pkg1.run

6. Edit the file /etc/X11/xorg.conf by typing:

sudo nano /etc/X11/xorg.conf

(if you don't have nano, "sudo apt-get install nano", unless you're happy to use vi instead)

7. change the line that says:

Driver        "nv"

to 

Driver         "nvidia"

8. quit

9. Type

sudo /etc/init.d/gdm start

And that should do it :)  (If you're lucky)

Cheers,

L.

---

### Post by jjbennee on 2005-09-29
Thanks!  It worked!

---

