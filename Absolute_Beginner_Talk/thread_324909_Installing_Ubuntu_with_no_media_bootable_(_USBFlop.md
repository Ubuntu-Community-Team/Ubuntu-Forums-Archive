---
title: "Installing Ubuntu with no media bootable ( USB/Floppy/CD/Network )"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Xyem on 2006-12-24
Evening all,

I plan to install Xubuntu on my 700Mhz laptop which is quite crippled as it is second hand. It cannot boot from USB, it has no floppy drive and no cd-drive and no PXE capable network either. This narrows my installation options to.. oh yes.. the harddrive. ;)

I managed to install Winbloze on it by creating 2 partitions, the first one booted into a DOS prompt while the second contained a copy of the CD. Fedora Core was installed by plugging it into my desktop and switching it back ( FC then detected all the changes and all was well ). My previous attempt at installing Ubuntu that way ended up with X being unable to start because it hadn't be reconfigured.

With this previous experience in mind, I would like to do a local install. The question is, can I install Xubuntu from the harddrive and if so, how can I boot into the installer?

Please share your suggestions.

Thanks

---

### Post by Ocxic on 2006-12-24
maybe if you copied  the cd to a small pertition on you hard drive and booted that might work, I've never attempet this so I'm jnot sure if it will work.

---

### Post by rccharles on 2006-12-24
> **Xyem said:**
> Evening all,

I plan to install Xubuntu on my 700Mhz laptop which is quite crippled as it is second hand. It cannot boot from USB, it has no floppy drive and no cd-drive and no PXE capable network either. This narrows my installation options to.. oh yes.. the harddrive. ;)

I managed to install Winbloze on it by creating 2 partitions, the first one booted into a DOS prompt while the second contained a copy of the CD. Fedora Core was installed by plugging it into my desktop and switching it back ( FC then detected all the changes and all was well ). My previous attempt at installing Ubuntu that way ended up with X being unable to start because it hadn't be reconfigured.


Thanks

This link will give you many options:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Here is one that might be of use: 
"Installation/FromWindows - Installing Ubuntu from Windows without using floppies, a CD, or any other removeable media"

You can change to Xubuntu once you have installed ubuntu, or you could install the server version then add Xubuntu.


....
If you still have Fedora Core around, you could copy you X11 profile over to Ubuntu.
/etc/X11/xorg.conf

At least this is the name in Ubuntu.


Robert

---

### Post by Xyem on 2006-12-24
> Here is one that might be of use:
"Installation/FromWindows - Installing Ubuntu from Windows without using floppies, a CD, or any other removeable media"
The harddrive has been completely wiped in preparation for installation so this one is a no-go. Also, all the other options seem to require *something* like network, CD or floppy. None of these are options for me.

One possible option seems to be putting in a minimal Linux environment which is booted into on the first partition, then run the installer from the second partition. The question is, will Ubuntu allow me to completely remove the first partition in order to install it and resize/delete partitions once installed.

If Xubuntu will reconfigure itself upon being placed back into the laptop, I would just install Xubuntu using my desktop and move the harddrive. Does (X)ubuntu have this capability ( something like kudzu I guess? )

EDIT:
I am doing the "install on desktop, move harddrive" technique and hoping it works smoother than last time. I must admit, I am very impressed with the method behind installing Ubuntu. I am editing this on the very same PC which is installing it to the harddrive! I love it :D

---

### Post by Xyem on 2006-12-24
Same problem as the last time I installed Ubuntu that way. It doesn't reconfigure itself to its new environment. X now won't start. I even ran 'dexconf' which has changed the driver to 'vesa'. Still not working. Oh yeah, since when has not even being able to decide on what my username is ( in regards to capitalisation ) been "friendly". I like my name to be capitalised! :p 

Any more ideas on doing a local install?

---

### Post by Ocxic on 2006-12-25
I found this it should get you going
 [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by david_kt on 2006-12-25
> **Xyem said:**
> Same problem as the last time I installed Ubuntu that way. It doesn't reconfigure itself to its new environment. X now won't start. I even ran 'dexconf' which has changed the driver to 'vesa'. Still not working. Oh yeah, since when has not even being able to decide on what my username is ( in regards to capitalisation ) been "friendly". I like my name to be capitalised! :p 

Any more ideas on doing a local install?


The method I tried and work (but not so easy actually) is to remove the harddisk, and then plug it to another computer with CD-ROM, and install ubuntu. In case your other computer is normal desktop computer, you will need an adaptor to plug in the laptop harddrive.

After installation is completed, put back the harddisk to your old laptop. If the X environment do not start (complaining that it is not properly configured), run below command:

sudo dpkg-reconfigure -phigh xserver-xorg

It will automatically re-configure X to the new home. Restart it and hopefully it is ok.

Regards,
DK

---

### Post by Xyem on 2006-12-25
Thanks david_kt, that command worked nicely. Just a couple of questions.

Will Xubuntu be "missing" anything laptop related as it was actually installed on a desktop?
The splash/loading screen after grub is very very faint ( everything is otherwise fine, desktop and terminal.. ), is this intentional or a possible configuration error?

EDIT:
*lapses into shock* I cannot believe how EASY it was to set up wireless on my laptop.. *editing from it right now*. Did I have to mess with drivers? No. Did I have to install some stupid utility thing? Nope. Was it faster and easier than Window? Hell yes! :D

---

### Post by david_kt on 2006-12-27
[QUOTE=Xyem;1929080]Thanks david_kt, that command worked nicely. Just a couple of questions.

Will Xubuntu be "missing" anything laptop related as it was actually installed on a desktop?
The splash/loading screen after grub is very very faint ( everything is otherwise fine, desktop and terminal.. ), is this intentional or a possible configuration error?
=============================================================================================
DK:
The splash screen should be ok, as I did not remember what it is looks like. Because I just did it to experiment and remove it again immediately and I don't use Xubuntu. But there is possiblity that you are on "emulation mode", i.e. no suitable video driver. To check this, please run below command:

xvinfo

and see the output. If it say that:

no adaptors present

then, you need to install apropriate driver. To install approriate driver, you need to check your chipset, and then check the manufacturer website whether or not they provide linux driver. 

If you are unable to find suitable drive and you are not satisfied with default emulation performance, you could try to teak the configuration is. Run below command:

sudo gedit /etc/X11/xorg.conf

You can try to lower default depth under "Sreen" section. For example from:

DefaultDepth 24

To

DefaultDepth 16.

After playing around with this setting and you are lost and wanted the default setting again, just run again:

sudo dpkg-reconfigure -phigh xserver-xorg

Please let me know the result of above as I am also still learning.

Regards,
DK

---

### Post by Xyem on 2006-12-30
My apologies for not seeing your post earlier, I have been fighting with my wireless..

> To check this, please run below command:

xvinfo
It does indeed return 'no adaptors'

I have run 'sudo dpkg-reconfigure -phigh xserver-xorg' and tried to select the neomagic driver ( my chipset is Neomagics MagicMedia 256ZX ) but it causes X to not start. I am currently using 'vesa'.

As I am using Xubuntu > sudo gedit /etc/X11/xorg.conf doesn't work as Xubuntu uses Xfce instead of GNOME. Therefore the command would be > sudo mousepad /etc/X11/xorg.conf

I was unaware of 'xvinfo' and I think it may come in useful in some other situations. Thanks! :)

---

