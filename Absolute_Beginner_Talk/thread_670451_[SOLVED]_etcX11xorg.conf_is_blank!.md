---
title: "[SOLVED] \etc\X11\xorg.conf is blank!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-17
--------------------------------------------------------------------------------

This is my situation now:

I have installed Ubuntu 7.10 with the alternate cd. If I try to boot into ubuntu it stops at 
Running local boot scripts (\etc\rc.local)

If I type
sudo nano (or vim) \etc\X11\xorg.conf I just see a blank file!

If I try
sudo dpkg-reconfigure xserver-xorg 
I can't choose fglrx from the list (which someone told me to use).

If I do
sudo aptitude install linux-restricted-modules
something is installed

If I do
sudo apt-get install xorg-driver-fglrx
it complains that it doesn't work.

Any suggestions?
__________________

---

### Post by dstew on 2008-01-17
> If I type
sudo nano (or vim) \etc\X11\xorg.conf I just see a blank file!
Are you doing this from the LiveCD? If so, you are not seeing the file that is on the hard disk, but the blank file in the LiveCD. To see the hard disk files from the LiveCD you have to mount hard disk file system to the LiveCD file system:```
sudo mkdir /mnt/hard_disk
sudo mount -t ext3 /dev/sda1 /mnt/hard_disk
sudo nano /mnt/hard_disk/etc/X11/xorg.conf
```

---

### Post by Rocket2DMn on 2008-01-17
First, your slashes are going the wrong direction - it's the opposite of windows, the command would be
```
sudo nano /etc/X11/xorg.conf
```
Once in the GUI you can enable restricted drivers from System->Administration->Restricted Drivers Manager

see here as well - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Mats_swe on 2008-01-17
> **Rocket2DMn said:**
> First, your slashes are going the wrong direction - it's the opposite of windows, the command would be
```
sudo nano /etc/X11/xorg.conf
```
Once in the GUI you can enable restricted drivers from System->Administration->Restricted Drivers Manager

see here as well - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I noticed.

This is my situation now:

I have installed Ubuntu 7.10 with the alternate cd. If I try to boot into ubuntu it stops at 
Running local boot scripts (\etc\rc.local)

If I do
sudo aptitude install linux-restricted-modules
something is installed

If I do
sudo apt-get install xorg-driver-fglrx
it complains that it doesn't work. It says:
Could not resolve gb.archive.ubuntu.com
Failde to fetch [http://gb.archives.....etc](http://gb.archives.....etc).


Any suggestions?
__________________
__________________

---

### Post by Digger78 on 2008-01-17
I have a suggestion, forget about the restricted drivers until you have a working desktop

```
sudo dpkg-reconfigure xserver-xorg 
```

choose the "vesa" driver

when you get back to the command line enter

```
startx
```

if it fails to start, take not of what is said (i think the last 5 or 6 lines) and post it here as accurately as possible.

---

### Post by Rocket2DMn on 2008-01-17
Sounds like either the repository is down or something is wrong with yout internet connection.  I suggest reconfiguring X like Digger suggested.  You can choose the open source "ati" driver instead of the restricted driver.  What video card do you have?  Most people don't need the restricted drivers, the open source ones work pretty well (I use the ati open source driver myself).

---

### Post by Mats_swe on 2008-01-17
I have ATI Radeon X1200 Video Card.

btw. I can't get into the GUI as someone suggested - that's the problem.

---

### Post by Rocket2DMn on 2008-01-17
That's why you reconfigure X.  It appears you can get to a terminal either by default or in recovery mode, so run
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware - do your best to answer.  When asked, select either the "ati" driver (open source) or vesa (a more generic driver).  At the screen resolutions page, use TAB to move and SPACEBAR to select and choose your monitor's highest resolution and everything less.
After you finish the reconfiguration, run
```
startx
```
or you can restart gnome
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by Mats_swe on 2008-01-17
> **Rocket2DMn said:**
> Sounds like either the repository is down or something is wrong with yout internet connection.  I suggest reconfiguring X like Digger suggested.  You can choose the open source "ati" driver instead of the restricted driver.  What video card do you have?  Most people don't need the restricted drivers, the open source ones work pretty well (I use the ati open source driver myself).

The ati or the vesa driver don't work.

The internet connection is fine for windows vista.

---

### Post by Rocket2DMn on 2008-01-17
I know the internet could work ok in vista, but it might need to be configured in linux.  Let's get a GUI first, then it's easier to troublshoot the internet and drivers.  SOME video driver must work, even if it's just VESA at 800x600 for now, run the reconfiguration and see what happens.

---

### Post by Mats_swe on 2008-01-17
> **Rocket2DMn said:**
> I know the internet could work ok in vista, but it might need to be configured in linux.  Let's get a GUI first, then it's easier to troublshoot the internet and drivers.  SOME video driver must work, even if it's just VESA at 800x600 for now, run the reconfiguration and see what happens.

I have done the reconfiguration so many times now. I just tried VESA and with 640x480 - didn't work. No matches found. Found screen but no useable configuration.

---

### Post by Digger78 on 2008-01-17
Do you have onboard graphics and an ati card?

---

### Post by Mats_swe on 2008-01-17
> **Digger78 said:**
> Do you have onboard graphics and an ati card?

I have a Fujitsu-Siemens Laptop Amilo Pa2510 [http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf]("http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf")

My Video Card is Radeon X1200.

How can I bypass the rc.local script? I mean it doesn't do anything.

---

### Post by Mats_swe on 2008-01-18
It finally worked:

[http://ubuntuforums.org/showthread.php?p=4161343#post4161343](http://ubuntuforums.org/showthread.php?p=4161343#post4161343)

---

### Post by Digger78 on 2008-01-18
Excellant, I'm glad you got it fixed.

Please mark this thread as solved  (thread tools)

---

