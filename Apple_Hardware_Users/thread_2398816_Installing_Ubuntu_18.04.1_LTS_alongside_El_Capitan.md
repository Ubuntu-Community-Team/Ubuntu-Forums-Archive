---
title: "Installing Ubuntu 18.04.1 LTS alongside El Capitan on MBP5,4"
date: 2018-08-17
forum: Apple Hardware Users
---

### Post by antisthenes2 on 2018-08-17
Hello everyone,

After the install (as described in the title), the following do not work: the iSight camera[1], the sleep function when closing the lid[2] and the  brightness keys/slider. The only proprietary driver that's installed is  that of the Wi-Fi (I also installed the proprietary nVidia driver to see  if it would make a difference, but it didn't, so I removed it). **How can I solve these issues?**

On a different note, **on which partition do you recommend installing the boot loader?**  I installed it on the Ubuntu root partition, but I’ve read that others  installed it on the hard disk.

Thanks!

[1] The camera did work when running Ubuntu from the live  USB.
[2] This function did work once when I  restarted the computer after the installation had completed.

---

### Post by aysiu on 2018-08-18
If you are going to install Ubuntu on a Mac, install grub to the Ubuntu partition. Then use something like rEFInd to select which disk to boot to.

That said, I'd recommend installing Ubuntu as a VM on the Mac instead of as a partition.

---

### Post by antisthenes2 on 2018-08-19
Do you know how I can solve the three issues mentioned in the OP?

---

### Post by aysiu on 2018-08-20
No idea. The documentation on that is scant and outdated: [https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)

---

### Post by lucawin on 2018-08-22
> **antisthenes2 said:**
> Hello everyone,

After the install (as described in the title), the following do not work: the iSight camera[1], the sleep function when closing the lid[2] and the  brightness keys/slider. The only proprietary driver that's installed is  that of the Wi-Fi (I also installed the proprietary nVidia driver to see  if it would make a difference, but it didn't, so I removed it). **How can I solve these issues?**

On a different note, **on which partition do you recommend installing the boot loader?**  I installed it on the Ubuntu root partition, but I&#8217;ve read that others  installed it on the hard disk.

Thanks!

[1] The camera did work when running Ubuntu from the live  USB.
[2] This function did work once when I  restarted the computer after the installation had completed.

Hi there, I recently installed Ubuntu on my Macbook and I followed [this guide]("https://wiki.ubuntu-it.org/Installazione/UbuntuMacIntel") and everything worked perfectly (I know it is written in Italian, but it is just to give you complete info about what exactly worked for me). As you can guess by giving a look at the guide, I installed rEfind and it worked just fine, no problems at all at booting and both Ubuntu and MacOS are now perfectly recognized by my bootloader.

[¹] I perfectly understand your problem with the iSight camera. I can tell you that I am pretty sure that just as the camera was working when you ran Ubuntu from the live USB, I can assure you that it was probably working when you installed Ubuntu on your HD _before_ you decided to try the Nvidia drivers; they are to blame, even if you removed them. They probably messed up the things a little bit.
[³] As for the brightness, also here the nvidia drivers are to blame. I don't know if you noticed, but _before_ you installed the nvidia drivers, the brightness controls worked. 

I would probably try the following in order to restore the nouveau driver:
```

sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
sudo apt-get install nouveau-firmware
sudo dpkg-reconfigure xserver-xorg
```

This should restore your system to the situation before the nvidia drivers installation.
I personally decided to keep the nvidia drivers installed and found a way to solve problems [¹] and [³] despite the nvidia drivers. In case you need, feel free to ask. I'll have to try to remember the exact steps I did to make those things work (I tried lot of things, but most of them didn't work), but I think its doable.

As for problem [²], I still have to find a solution myself.

EDIT: 
As I told you, I think everything should work if you got to make Ubuntu "virgin" again. I am pretty sure that the problems are due to the nvidia drivers, so I would recommend to follow the next steps only in case 1) you weren't able to make Ubuntu virgin again, or 2) you decided to use the nvidia drivers:
- [this is the guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight") I followed in order to make the iSight camera work with my nvidia drivers; this time in English!
- I followed [these steps]("https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver") as suggested by the User Chris Pearce to make the brightness controls go back to work after the installation of the nvidia drivers;

---

