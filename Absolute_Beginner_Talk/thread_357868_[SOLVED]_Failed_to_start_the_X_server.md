---
title: "[SOLVED] Failed to start the X server"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by freddybob on 2007-02-10
Help!  This morning I downloaded the most recent updates, after installing I was prompted to restart.  But when I did I got a message saying "Failed to start the X server".  Now I can't get back into Ubuntu!

How do I fix this?

I'm running Edgy Eft with the nvidia video driver.

---

### Post by Unity on 2007-02-10
If you have used Envy to install your NVIDIA driver , just use ctrl+F1 , login and then type Envy. 

Dunno if it's the best solution or not , but it has worked for me each time :)

---

### Post by arochester on 2007-02-10
This happend to me as well. Nvidia gone too.

At the command line prompt input:
> sudo dpkg-reconfigure xserver-xorg
This will start a text based wizard. If you do not know the answer to any questions go with the suggested default answer. This should restore functionality.

---

### Post by freddybob on 2007-02-10
Thanks, but I didn't use Envy (never heard of it).

---

### Post by arochester on 2007-02-10
Check out Envy. It finds out which video card is installed, downloads and installs the correct driver for Nvidia or ATI. Read about it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by freddybob on 2007-02-10
> **arochester said:**
> sudo dpkg-reconfigure xserver-xorg

Thanks, I tried this, accepted all the default options in the wizard.  When it ended I restarted the machine, but X server still failed.  I'll try again selecting different options.

---

### Post by PartisanEntity on 2007-02-10
Check out the last 10 or so pages of this thread:
[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by Zzl1xndd on 2007-02-10
Im getting the samething accourding to the log the error I have is

failed to load module "wfb" (module does not exist, 0)

Error:api mismatc: the NVIDIA kernel module 1.0-8776, but this X module has version 1.0-9746. Please make sure that the kernel module and all NVIDIA driver compnents have the same version.

---

### Post by meborc on 2007-02-10
if the upgrade installed a new kernel, then you might need to reinstall the nvidia drivers...

to do that boot your machine... when x fails do the dpkg-reconfigure xserver-xorg... chose VESA as your vide driver... then startx

you SHOULD be able to see gnome/kde/xfce again... only without the 3d acceleration... now reinstall the nvidia drivers and reboot

i hope this works... haven't upgraded my edgy machine yet

:)

---

### Post by SirPecanGum on 2007-02-10
By your description I have suffered the same problem and fixed it, seemingly, by going to Synaptic and installing the Nvidia stuff to match the new kernel update/s. 

I hope this works for you (et al too), or at least I hope it doesn't make it any worse for you!

BTW, you can get to a working desktop by selecting a previous kernel on your boot menu.

---

### Post by Zzl1xndd on 2007-02-10
ok im back in but im having a stupid momnet what do i do to get my Nvidia drivers back.

---

### Post by arochester on 2007-02-10
Download Envy. It's a .deb. Right click in it and install.

---

### Post by Zzl1xndd on 2007-02-10
Thanks man that DID the trick. Thats why I love Ubuntu :).

---

### Post by mikewhatever on 2007-02-10
I'd say, go back to the old kernel. Hopefully, after so much tinkering, it still works. I this morning, exactly the same issue, and reinstalling nvidia driver with envy brought GUI back, but, there was no wireless, and wrong screen resolution. Having no more time to invest in this, I've reverted back to the old kernel and reinstalled nvidia driver again. Grub menu had to be edited, since the default OS to boot has changed, and also, I didn't want the two new kernel entries to appear at boot. I have to say, it was kind of fun. Not having heard of envy before, I am glad I've discovered and used it. This should be a good lesson to all of us, not to expect too much.

---

### Post by Zzl1xndd on 2007-02-10
Doing the same now just realized the beryl isnt working right. But thats kool Ill wait a little bit I always warn people about upgrading too soon and what do I do?

---

### Post by freddybob on 2007-02-10
Here is how I solved the problem...

1. after the "Failed to start X server" message I got to the command prompt and entered "sudo dpkg-reconfigure xserver-xorg"

2. I accepted all the default values in the reconfigure wizard **except** that I chose VESA as the video driver (thanks meborc)

3. when that was completed I rebooted the machine and was able to get back into Ubuntu - but without 3D acceleration

4. I then downloaded and ran Envy following the simple instructions on this page: **[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)** (thanks Unity & arochester)

5. my system is now back to normal

Thank you!

As a newbie to Ubuntu a problem like this could have put me off Linux for life, but the amazing helpfulness of everyone on this forum, not to mention how quickly you all responded, was fantastic.  Do you all know how great you are?  ;)

---

### Post by mrbungle on 2007-02-10
this also worked for me :) 

is this some kind of bug? why does this keep happening and will there ever be a fix for it?

---

