---
title: "What cmd is used for info on graphic driver?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Dan-O on 2008-03-27
Halp me out guys.

What is the terminal command or area to look for the current video driver for my computer?

On the Ubuntu for Dell Inspiron 1501, Red says that we should be using ATI's 2.1.7281 fglrx driver.  I'm not sure which one I have.  

Thanks
Dan-O

---

### Post by philinux on 2008-03-27
cat /etc/X11/xorg.conf

there should be a grep in that but tired. Memory lapse

---

### Post by Oldsoldier2003 on 2008-03-27
> **philinux said:**
> cat /etc/X11/xorg.conf

there should be a grep in that but tired. Memory lapse
 
```
fglrxinfo
``` should return the driver version. at least it does for ATI Cards. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Dan-O on 2008-03-27
Many thanks for the quick response.

I'm sure I am going to need some more help.  I downloaded the gutsy a few days ago.  I was pleased with the grub and dual boot install....flawless.

I downloaded the latest and greatest proprietary ATI drivers for my Dell Inspiron 1501.  I enabled the driver and my video didn't look so hot after reboot.

So, I went into the etc/X11/ folder and renamed my backup file to the xorg.conf in order to revert back to the original settings.  All good.  Back to normal.

Today, I upgraded to Hardy Heron......sooooo incredibly smooth i almost slapped my momma.

Well, It looks like Hardy is able to use this driver and now, when I enable it in my "Hardware Drivers" it says, "Enable" but, "not in use".

Any ideas how I should proceed?

---

### Post by OffAxis on 2008-03-27
(follow up to Oldsoldier2003's comment above)

```
dpkg -l nvidia*
```

will return everything nvidia, install status, and their versions.
nvidia-glx-new and nvidia-glx-legacy are the listings for the driver.

```
nvidia-settings 
```

may also return a version number for the driver (I'm away from my machine at the moment).

---

### Post by OffAxis on 2008-03-27
```
sudo dpkg-reconfigure xserver-xorg
```

will take you through the xserver configuration utility (where you can choose the driver).

Instead of doing the download and install yourself, you might try envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

For future reference (I'm not entirely certain if this is the way you did it), doing the download and install yourself is the hard way. Using the 'Restricted Driver' checkbox in the System Settings is the easiest method of getting the proprietary driver.

---

### Post by Dan-O on 2008-03-27
Offaxis

That helped me some.  Unfortunately, when I try to re-enable the driver in the Hardware, then reboot...it crashes and says no bueno.

I may be looking at re-installing.

---

### Post by Dan-O on 2008-03-27
Here is what I am getting:

E:ERROR: could not create configuration directory in /home/root/.synaptic-mkdir (2 No such file or directory)

---

### Post by forrestcupp on 2008-03-27
If you installed Envy, boot to the recovery mode and type
```
envy --uninstall-all
```
If not, type
```
apt-get --purge remove xorg-driver-fglrx*
```
Then do this again and choose Vesa drivers
```
dpkg-reconfigure xserver-xorg
```
After you're done with the settings restart into X
```
exit
```

Then use the Restricted Drivers Manager to install the ATI drivers.  You don't need Envy right now for Hardy because it has the latest drivers in the Restricted Drivers Manager.

---

