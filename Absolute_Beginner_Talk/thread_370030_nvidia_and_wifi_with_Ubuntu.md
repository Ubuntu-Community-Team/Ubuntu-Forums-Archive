---
title: "nvidia and wifi with Ubuntu ?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by elmerfud on 2007-02-25
How are the nvidia drivers handled in Ubuntu ?  Same as Fedora, download the script from nvidia and run it ?  

How is wifi handled in Ubuntu ?  Download ndiswrapper and run it ?  I have a Broadcom card that works well with ndiswrapper.

---

### Post by terdon on 2007-02-25
Hi,
   ubuntu should actually recognise and install the nvidia drivers automatically (just add the universe and multiverse repositories in synaptic)

As for wifi, to my great surprise it recognised and configured my wlan card without needing ndiswrapper! In fact it now works better than under windows. All other distros I've tried have needed ndiswrapper for this card...

Try it, my guess is it will recognize everything by itself.

---

### Post by Bachstelze on 2007-02-25
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by elmerfud on 2007-02-25
Thanks for the replies.

I am typing this from 6.10 Live, BTW.

---

### Post by elmerfud on 2007-02-26
So I backed up my Fedora drive today and installed Kubuntu.

I just installed the Nvidia driver as per the HowTo.  I couldn't find a legacy driver and my video card supposedly needs it.  I installed the non legacy driver.  The xorg config processor worked without any errors.  I restarted my computer and the display came up on both monitors like it should. (I run dual monitors.)

The Only problem is that the desktop area is way too big for the monitors.  Its like in Windows when you try to run 800x600 on a 640x480 screen.  How do I fix this ?

The other thing I am not sure about is the monitor hardware.  The primary monitor is a 1680x1050 laptop display.  The secondary monitor is a Dell FPW2005.  When I select those monitors at the bottom of the page it states "This configuration cannot be safely tested".  Sounds like I have the scan rates wrong ?

Help !

I looked in the xorg.conf file and its using the nvidia driver and everything.  Just the monitors are a little messed up.

---

### Post by elmerfud on 2007-02-26
Had to edit xorg.config.  Otherwise it was all automatic !  Excellent !
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

I had to remove every setting except the one I needed, 1680x1050.  Then it worked excellent. 

It took me 1/10th the time to set up nvidia this time that it did with Fedora the first time.  I hate that the nvida drivers are proprietary, but I like what Ubuntu did to make them easy to use anyway.  Good work.

---

### Post by elmerfud on 2007-02-27
I can't install ndisgtk on my machine without dependency errors and then I get a broken package in synaptic.   How do I handle that ?

Does apt-get have a list function that isn't in the man pages ?   Like yum has yum list... ?

Thanks.

---

### Post by elmerfud on 2007-02-27
I've got another issue.  The laptop monitor is fuzzy compared to how it was with Fedora core.  Its like the fonts aren't sharp or something.  They were in FC.  The second monitor is sharp.  I compared the xorg.config file and the modes are the same.

Any ideas ?  

Thanks

---

