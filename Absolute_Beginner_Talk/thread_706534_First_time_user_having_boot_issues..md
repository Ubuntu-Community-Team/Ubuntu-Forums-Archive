---
title: "First time user having boot issues."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by walk3rb0h on 2008-02-24
I just installed Ubuntu for the first time, I am able to boot to the CD just fine but for some reason booting off the HD just gives me a black screen. Please be patient im new to Linux. 
Is there something obvious im missing?

---

### Post by radiocognition on 2008-02-24
First, lets learn a little more about your computer:

-  Is Ubuntu the only OS on your system?
-  What version of Ubuntu do you have and how did you install it?
-  Did you have any errors during the install?
-  When you boot into the live CD, can you mount your hardive and see your previous Ubuntu install?

We want to help newer users out, but more information about your system and particular problem would help us identify and correct your issue faster

---

### Post by deepclutch on 2008-02-24
^that means the bulletproof X failed.in simple,X(display) is not able to support ur graphics card whether onboard or not.

we can help,if u give the specs of ur PC esp mobo,graphics card and Monitor with size.
meanwhile u can edit /etc/X11/xorg.conf section"device" to use "vesa" driver ;)

---

### Post by walk3rb0h on 2008-02-24
monitor = Samsung SyncMaster 940BW  19" widescreen

Processor = AMD 3200+

Video = Radeon x1800xt  by visiontek

The motherboard is an nForce3,  Made by Gigabyte ga-k8nsc-3349 is the model number.

HDD is a seagate barracuda 120 gig  model - ST3120026AS

I have 2gig dual channel Kingston PC3200

---

### Post by Rocket2DMn on 2008-02-24
You need to reconfigure X, then you will probably want to install the restricted drivers.
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
then install fglrx proprietary ati drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by walk3rb0h on 2008-02-24
Looking in the device manager I am seeing unknown for the drivers for the host to PCI bridge

---

### Post by deepclutch on 2008-02-24
^amd ati gfx card support is bad,u need to complete the installation,then get "fglrx" driver(search this forum) for 3D and full support(prorprietary driver)
so,inorder to complete,
when the black screen is seen,press CTRL+ALT+F1 to get a terminal("#" prompt).
edit using **nano** editor,the /etc/X11/xorg.conf as:
```
nano -w /etc/X11/xorg.conf
```
press ^up and v down arrow to browse the file.
go to section "device"
change the line with:```

Section "Device"

    Identifier     "...."
    Driver         "**[COLOR=Red]vesa[/COLOR]**"
EndSection

```
save the file by pressing CTRL+X and press "y" on asking to save changes :)
now,in the same terminal,do below command:
```
/etc/init.d/gdm restart 
```
reply back !

---

### Post by MasterJS on 2008-02-24
I think what he's talking about is what a lot of people are having problems on. He might not be seeing the loading bar and getting to the login screen probably takes about 5 minutes. The original poster might now have waited long enough to find out. If what i'm talking about is the case, then he needs to change the resolution of the USplash screen (the loading bar). This is probably due to the fact that his screen is too big for the 800 x 600 resolution of the Boot Screen.

---

### Post by walk3rb0h on 2008-02-24
I have now tried everything you guys have suggested and still get a black screen, I am not even able to get up a terminal.. So at this point im lost completely.. Able to boot to the CD fine. Thats how im posting on here..

---

### Post by walk3rb0h on 2008-02-24
I was able to get into a terminal booting into recovery mode however the xorg.conf file appears to be blank.. nothing to edit.

---

### Post by Rocket2DMn on 2008-02-24
If there is no xorg.conf, you need to generate one, try the automatic method:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
make sure you're looking in the correct directory (case sensitive)
/etc/X11/xorg.conf

---

### Post by mivo on 2008-02-24
Actually, the first thing I'd do is to change the boot options. Interrupt Grub during boot, select (e)dit, and add *nosplash* to the boot options. Also remove *quiet.* This will get you at least a useful error message. :)

---

### Post by walk3rb0h on 2008-02-24
> **mivo said:**
> Actually, the first thing I'd do is to change the boot options. Interrupt Grub during boot, select (e)dit, and add *nosplash* to the boot options. Also remove *quiet.* This will get you at least a useful error message. :) ok first off.. HUH?

Anyways update : after getting to the black screen If I do ctrl/alt/f1  It will finish booting to the logon and I'm able to get into the OS.  I ran all the updates and enabled the ATI drivers. After the reboot still same effect but doing the ctrl/alt/f1 seems to get around it..

---

### Post by mivo on 2008-02-24
Okay, try this:

After successfully logging in, press Alt+F2 and type:

**gksu gedit /boot/grub/menu.lst**

This will open the text editor (with root access). Scroll down to where it says, "## ## End Default Options ##". In the next paragraph, look for the line that starts with "kernel". Here, replace "quiet" with "nosplash". The paragraph will look similar to this:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=68f63350-fb5a-44b2-bb11-681324d9e6fa ro irqpoll nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

It may not look exactly like this. Don't try to make it match exactly, it's only a sample. Just make sure that it does say "noplash" instead of "quiet". Save the file and reboot. Instead of the blank screen you should see a lot of system messages, and then the login screen. :) If this does not work, repeat the above process and also add "irqpoll" (as shown above).

---

### Post by walk3rb0h on 2008-02-24
That seems to have worked thanks.. No I have to figure everything else out.. should I be worrying about drivers at all?

---

### Post by mivo on 2008-02-24
If you installed the driver from *System -> Administration -> Restricted Drivers Manager*, you should be fine. I'm not exactly sure what exactly is causing the trouble you have (and me, too, but I have an Nvidia card), I only know how to work aorund it so that it is no longer a problem. ;)

---

