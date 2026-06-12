---
title: "Nvidia drivs isntalled - but failing"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-27
I've downloaded the nvidia 1.0-7667 drivers for Linux to make my GeForce 4 Ti4200 work. The installation goes fine, it compiles a driver and then I get the nvidia logo and X starts fine. If I reboot it's fine. If I use Linux for a while and reboot it's not fine and I have to reinstall it again.

This is how I install the driver:
1. I open a terminal and type "sudo killall gdm". This kills X.
2. sudo sh /home/kamine/NVIDIA/NVIDIA-Linux-x86-1.0-7667-pkg0.run (I have a pkg1 too)
3. It looks for a pre-build kernel but doesn't find any.
4. It compiles a kernel for me.
5. The install is finished.
6. gdm (too start X)
7. change xorg.conf to "nvidia"
8. Reboot.

Then I restart a bit later and X refuses to boot.

And when it crashed I switch to my VESA-using backup with "sudo cp /etc/X11/xorg.conf_vesa /etc/X11/xorg.conf".

What is causing this? How do I fix it?

---

### Post by apollo2011 on 2005-06-27
The first thing I am noticing is that you are using the driver from the nvidia site.  Ubuntu comes with one, it just isn't installed with the base system.  You should be able to follow the steps in the Wiki page linked below.  Ignore the XMMS error, the page hasn't been edited and that is old and the bug has since been fixed.  Other than that, you should be able to install the driver and get 3D support for playing games etc.

Scroll down on that page to the Nvidia Graphics Card section past the ATI section.

[https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29)

---

### Post by Trojan1313 on 2005-06-27
[QUOTE=apollo2011]The first thing I am noticing is that you are using the driver from the nvidia site.  Ubuntu comes with one, it just isn't installed with the base system.  You should be able to follow the steps in the Wiki page linked below.  Ignore the XMMS error, the page hasn't been edited and that is old and the bug has since been fixed.  Other than that, you should be able to install the driver and get 3D support for playing games etc.

Scroll down on that page to the Nvidia Graphics Card section past the ATI section.

[https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29)[/QUOTE]
 I was told not to use that one 'cause the official one works better. :)
Think I got it working now though. :)

For reference to people with simmilar problems:
Uninstal the free driver included in Ubuntu and reinstall nvidias driver.

Sorry for not updating the thread, I just got it working before I saw you answer. :) Thanks anyway.

---

### Post by apollo2011 on 2005-06-27
I'm not sure who told you that, but the stock Ubuntu driver worked fine for me and I haven't had any problems with it since I set it up...

---

### Post by TristanMike on 2005-06-27
I've had no problems either using the drivers I installed off of ubuntuguide.org, I even like the Nvidia splash screen.  In fact, you might want to do a search for Nvidia cause I might be wrong, but I thought other people were having issues with the 7667 drivers released off of the Nvidia site.  I myself have just stuck with the ones included.  Hope this helps
TristanMike

---

### Post by Trojan1313 on 2005-06-28
Okay, it seems the drivers didn't work now either, and I have no idea what to do anymore. Not even a fresh install of the drivers work. :(

---

### Post by Trojan1313 on 2005-06-28
Okay, so now I've reviewed the error log X gives me, and it would seem that the driver doesn't think that any of the resolutions are in range for hsync and vrefresh. =/

---

### Post by apollo2011 on 2005-06-28
Well did you ever try the drivers that come with Ubuntu? Even if you have you might try it again and follow the HOWTO I linked you to before

---

### Post by Trojan1313 on 2005-06-28
[QUOTE=apollo2011]Well did you ever try the drivers that come with Ubuntu? Even if you have you might try it again and follow the HOWTO I linked you to before[/QUOTE]
 Used those last time I installed. Searched for nvidia in synaptic this time. And it didn't work.

Was it a faulty assumption that it was because of the old drivers?

---

### Post by apollo2011 on 2005-06-28
Strange again.  I just did the same and got all the nvidia packages.

---

