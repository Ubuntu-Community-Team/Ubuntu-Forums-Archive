---
title: "ARGH! This is bad.."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Snoo on 2007-07-02
Hello.

I was trying to get my browser sound working, which I did. I then installed 'Democracy TV' which crashed. Now Ubuntu (Fiesty) won't boot up. There is apparently a problem with X Server and GDM won't load.

I looked at the info and it seems to point to /etc/x11/xorg.conf

Can anybody help. I'm stuck at a command line whenever I try to boot. I can log-in via it but it won't run the GDM front end.

Tried recovery mode with no joy either.

---

### Post by Rocket2DMn on 2007-07-02
Get to terminal from login screen by doing ctrl+alt+f1 (if you're not already at a CLI) and reconfigure your xserver by running:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Snoo on 2007-07-02
I tried this. Hit OK, quite a few times (didn't really know what it all meant).

It's still broken. I'm not sure if it's broken more or less but X Server is still disabled.

---

### Post by nitro_n2o on 2007-07-02
If you have a back up of ur xorg.conf use it
if not try to use the attached file... 
just rename it to xorg.conf and put it in /etc/X11/ 
What is your graphics card?

---

### Post by Rocket2DMn on 2007-07-02
When you reconfigure, you actually need to read it and know what it's asking you, esp. for the display stuff.
You can see if there are older backups of the xorg.conf file in the /etc/X11/ directory and restore one.  The backups are in the format of something similar to xorg.conf.YearMonthDayTime (or some variation on that).
To restore:
```
sudo cp /etc/X11/xorg.conf.numbersHere /etc/X11/xorg.conf
```
Be sure to select a file that predates your Democracy TV install.

---

### Post by Snoo on 2007-07-02
> **Rocket2DMn said:**
> When you reconfigure, you actually need to read it and know what it's asking you, esp. for the display stuff.
You can see if there are older backups of the xorg.conf file in the /etc/X11/ directory and restore one.  The backups are in the format of something similar to xorg.conf.YearMonthDayTime (or some variation on that).
To restore:
```
sudo cp /etc/X11/xorg.conf.numbersHere /etc/X11/xorg.conf
```
Be sure to select a file that predates your Democracy TV install.


THanks mate.

I realise I was being a d*ck not reading it all but I'm tired and have had 2 days of fixing car problems. I'll have  a more sensible go tomorrow. x

---

### Post by Rocket2DMn on 2007-07-02
Not a problem, let us know if you keep having problems - I or somebody else will be around to help.

---

### Post by Snoo on 2007-07-06
OK. Finally got around to looking at this.

1. My graphics card is a Radeon X300 series. That doesn't appear to be on the list for the reconfigure in Xserver

2. Can somebody give me a few basic DOS type commands so I can change directory, and scroll the file directory 1 page at a time? Can't seem to find the /etc/X11 directory.

Thanks,

---

### Post by Snoo on 2007-07-06
OK. I'm over that little hurdle. Basically I don't have a good back-up of xorg.conf

I guess I can use the one supplied up above, but that will be on the XP side of my dual boot (where I'm now posting from) and I need to copy it into the right place.

Can anybody assist with that? I'm sure I can look into my XP file system from linux but I don't know where to start digging.

Thanks

---

### Post by lbelloq on 2007-07-06
Anyone out there, is it possible to automount a USB pendrive in CLI?

---

### Post by Rocket2DMn on 2007-07-06
> **Snoo said:**
> OK. I'm over that little hurdle. Basically I don't have a good back-up of xorg.conf

I guess I can use the one supplied up above, but that will be on the XP side of my dual boot (where I'm now posting from) and I need to copy it into the right place.

Can anybody assist with that? I'm sure I can look into my XP file system from linux but I don't know where to start digging.

Thanks

You can read into your linux filesystem using the driver from [www.fs-driver.org](www.fs-driver.org).  It's a sweet little addon that lets you read/write the ext3 file system on your dual boot machine.  You will need to reboot after installing it.
Your xorg.conf file will be found in /etc/X11/ directory of the ext3 filesystem as seen from windows.
I don't really suggest using other people's xorg.conf files because they are built specifically for certain machines, but it seems you stand little to lose right now.  Just make sure you save your old one with a different name so you can use it later if necessary.



when you do the reconfigure like we talked about earlier, you should just be able to select the "ati" driver.
If this doesn't work you may want to use the restricted drivers:
   From windows (with fs-driver installed) you can open the file /etc/apt/sources.list
      Once here you need to "uncomment" the lines related to restricted drivers (remove the # sign in front of the appropriate lines).
   Then, back in the linux command line, you can install the fglrx drivers:
```
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
```
Then reboot the computer (into Ubuntu again), and you should hopefully have a GUI.

---

### Post by Rocket2DMn on 2007-07-06
> **lbelloq said:**
> Anyone out there, is it possible to automount a USB pendrive in CLI?

You should have created a separate thread for this, this current thread has nothing to do with mounting drives.  If automount is enabled, you should be able to access your usb pen drive in /media/disk/
If this doesn't work, please start a new thread about it.

---

### Post by Snoo on 2007-07-06
> **lbelloq said:**
> Anyone out there, is it possible to automount a USB pendrive in CLI?


That would be good as I have one and can fire the file on from XP. I'm really stuck just firing hand written code into a command line without much of a clue. Reconfiguring xonf is doing nothing and I'm sure I'm doing it properly now. I feel I'm just going to have to format the whole drive soon and be done with it... :desperate:

---

### Post by Snoo on 2007-07-06
Thanks Rocket. Just reading up your post now.

---

### Post by Snoo on 2007-07-06
> **Rocket2DMn said:**
> 
   From windows (with fs-driver installed) you can open the file /etc/apt/sources.list
      Once here you need to "uncomment" the lines related to restricted drivers (remove the # sign in front of the appropriate lines)..


Which lines relate to the restricted drivers?


> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#AUTOMATIX REPOS END


---

### Post by Rocket2DMn on 2007-07-06
any of those lines with "restricted" in it, but it looks like it's all good to go.  the only restricted repositories that are still commented date back to Edgy (the previous release of Ubuntu), so don't worry about them.
Do not modify this file - it's already OK.
Now you can proceed to rebooting into Ubuntu and installing the fglrx stuff.  If no GUI appears when you reboot, type "startx".  If still not, run the reconfiguration again and see if "fglrx" is an option for video driver and select it.

---

### Post by Snoo on 2007-07-06
Rocket, I'm In!!!

Thank you so Much!


Only thing is my resolution is a bit large and blurry. Highest resolution I can select from the preferences is 1024x768 @60Hz It won't let me go higher. Do I have to go back to xorg and play around?

monitor is a HP 1740. 
THanks

---

### Post by Rocket2DMn on 2007-07-06
Yeah, you select the resolutions in the reconfiguration.  When you get to that portion of the configuration, you can move through the different resolutions by hitting TAB and using SPACEBAR to enable a particular resolution.  You should enable the highest resolution your monitor can support and everything less than that.   You can then choose which one you want once you get back to the GUI under System->Preferences->Screen Resolultion (I believe - not in front of my linux box to double check that).

---

### Post by Snoo on 2007-07-06
OK. I selected 1280x1044 in config (checked my monitor with manufacturer) but when I go into screen resolution I don't get that opiton. The highest is still 1024x768

---

### Post by Rocket2DMn on 2007-07-06
Have a look at this, it might help: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252)

There is other stuff on that page that might be useful, too.  Check around.  Also, make a backup of your xorg.conf file right now since we got it working
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

