---
title: "Ati 3D acceleration problems"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by white_eagle-mk on 2008-01-18
Please help me! First I had the usual ATi drivers from the restricted drivers manager, then in hopes I to get hibernate back on my laptop (I hate turning off) I installed envy, and via envy I installed the ATi Catalyst drivers the latest version, Compiz again works fine but; when I try to run a 3D acceleration app. like Celestia, Stellarium, Google Earth, Neverball etc. my computer just logs off and I have to log back in. I tried removing xorg-server-fglrx which showed me that it will remove other packages too, I accepted and the next day when I started my computer it couldn't start GNOME, it started the X-Server, all I did is via envy textual interface, I again installed the ATi drivers and now I'm thinking of complete format of the computer:(, but before I do this, I'm asking for help
Can I somehow REMOVE the ATi drivers and get back the old drivers which I can Install via the restricted drivers manager?!!? :mad:

---

### Post by jeffus_il on 2008-01-18
> **white_eagle-mk said:**
> Please help me! First I had the usual ATi drivers from the restricted drivers manager, then in hopes I to get hibernate back on my laptop (I hate turning off) I installed envy, and via envy I installed the ATi Catalyst drivers the latest version, Compiz again works fine but; when I try to run a 3D acceleration app. like Celestia, Stellarium, Google Earth, Neverball etc. my computer just logs off and I have to log back in. I tried removing xorg-server-fglrx which showed me that it will remove other packages too, I accepted and the next day when I started my computer it couldn't start GNOME, it started the X-Server, all I did is via envy textual interface, I again installed the ATi drivers and now I'm thinking of complete format of the computer:(, but before I do this, I'm asking for help
Can I somehow REMOVE the ATi drivers and get back the old drivers which I can Install via the restricted drivers manager?!!? :mad:
When your computer "logs off" it is actually the X server which crashes, if it interests you. You do not have to uninstall to change the graphics driver, you must open a terminal    and edit the file /etc/X11/xorg.conf.
You wil find a line Like:
Device "fglrx"
If you change fglrx to another name run the xserver it will start with the new driver.
By the way you may have a backup copy of your old xorg.conf file.
do a "cd /etc/X11"
to move to the directory.
do a "ls -l xorg.conf*"
to see a file list.

Looking at the file dates  , you can choose a file to:
sudo cp xorg.conf.xxxxxx  xorg.conf

---

### Post by white_eagle-mk on 2008-01-18
> Device "fglrx"
If you change fglrx to another name run the xserver it will start with the new driver.

 What do you mean by changing fglrx to another name?

---

### Post by Ber P on 2008-01-18
Try changing it to "vesa", just to get the computer running again. Then using synaptic, you could remove all packages *starting with* fglrx, to completely remove fglrx-stuff. 
Reboot and switch on the restricted ATI driver. 
That has brought me back, when new ATI driver failes. 
After that I just wait for "next month" when a new driver is released from ATI. :(

---

### Post by white_eagle-mk on 2008-01-18
> **Ber P said:**
> Try changing it to "vesa", just to get the computer running again. Then using synaptic, you could remove all packages *starting with* fglrx, to completely remove fglrx-stuff. 
Reboot and switch on the restricted ATI driver. 
That has brought me back, when new ATI driver failes. 
After that I just wait for "next month" when a new driver is released from ATI. :(
Ber P, I changed it to vesa, and I removed every package starting with fglrx, I rebooted and I logged in, the computer logged in as normally in 1024*768 resolution and when I activated the restricted ATi driver via the restricted driver manager, I rebooted, and still the same happened!!!?!!?!?1 
Oh god, I wish I havent messed with the drivers earlier

---

### Post by Ber P on 2008-01-19
Try removing all old fglrx drivers with ```
sudo /usr/share/ati/fglrx-uninstall.sh
```
followed by ```
sudo apt-get remove xorg-driver-fglrx
```
You should probably boot up with "vesa" driver enabled and check that the restricted driver isn't active before running the commands.

By the way. You can see what version of the fglrx driver is installed with
```
apt-cache show xorg-driver-fglrx | grep Version
```
I think the repo version is 8.37

---

### Post by white_eagle-mk on 2008-01-19
It's no use :( I did everything as you told me, I rebooted, and the computer logged in as usually with 1024*768 resolution with compiz enabled, and that last command gives me this:
```
whiteeagle@whiteeagle-laptop:~$ apt-cache show xorg-driver-fglrx | grep Version
Version: 8.40.4-1
Config-Version: 8.40.4-1
Version: 7.1.0-8.37.6+2.6.22.4-14.10
Version: 7.1.0-8.37.6+2.6.22.4-14.9
```

Oh, and one more thing, my DVD-ROM/CD-RW can't read CD's or DVD's because its broken, I know whats the problem, and look at me: I am too lazy to give my laptop to someone to fix, or even better to buy a new DVD-RW optical drive. So, I'll have to fix this somehow, I can't stand booting my computer and not using Stellarium or G. Earh, or playing some good 3D game :( I need urgent help, if you can help me, if you can't, I'll just buy a new optical drive and reinstall Gutsy, thanks although!

---

### Post by Ber P on 2008-01-19
Well since you are still running 8.40, it's apparently not removing the 'new' driver version. Try out this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation"). It has worked very well for me. There are also some help about removing old drivers.

What does ```
fglrxinfo
``` show you? If it tells you something about MESA, then your direct rendering is not working. This isue is also coverd in the guide above.

You might also try out envy, [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html"). This is an automated ATI and nVidia driver update tool. People speak very nice about it. I haven't much experience with it my self.

---

### Post by white_eagle-mk on 2008-01-20
Ber P, problem solved! I followed the instructions at the bottom of the recommended page, I rebooted, went to restricted drivers manager, ticked the box, downloaded the software, rebooted, and lookie I got everything BACK!

---

