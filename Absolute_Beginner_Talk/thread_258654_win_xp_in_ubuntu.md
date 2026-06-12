---
title: "win xp in ubuntu"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Deonilin on 2006-09-16
I have just managed to install ubuntu on a usb hdd after a lot of hassle. Being an windows user for so long i would like to try and get either some sort of windows or windows emulation for programs i cannot find alternatives to in linux. As the linux install is a dual boot i was woundering if it was possible to load my current windows installation under linux and run it. alternativly will wine let me run programs that are currently installed on the windows partion.

It will be reading from a ntfs drive and i dont really want to reinstall windows and all my programs again.

---

### Post by MrHorus on 2006-09-16
> **Deonilin said:**
> I have just managed to install ubuntu on a usb hdd after a lot of hassle. Being an windows user for so long i would like to try and get either some sort of windows or windows emulation for programs i cannot find alternatives to in linux. As the linux install is a dual boot i was woundering if it was possible to load my current windows installation under linux and run it. alternativly will wine let me run programs that are currently installed on the windows partion.

It will be reading from a ntfs drive and i dont really want to reinstall windows and all my programs again.

```
sudo apt-get install wine
```

Then go and read a FAQ about wine :)

---

### Post by Ziox on 2006-09-16
> **Deonilin said:**
> I have just managed to install ubuntu on a usb hdd after a lot of hassle. Being an windows user for so long i would like to try and get either some sort of windows or windows emulation for programs i cannot find alternatives to in linux. As the linux install is a dual boot i was woundering if it was possible to load my current windows installation under linux and run it. alternativly will wine let me run programs that are currently installed on the windows partion.

It will be reading from a ntfs drive and i dont really want to reinstall windows and all my programs again.

If you computer is decent enough, I would suggest trying out VMware Server...it allows you to run a full-blown version of Windows inside Ubuntu...You just need the Windows CD for it to work...

awesome guide => [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by tagra123 on 2006-09-16
> **Ziox said:**
> If you computer is decent enough, I would suggest trying out VMware Server...it allows you to run a full-blown version of Windows inside Ubuntu...You just need the Windows CD for it to work...

awesome guide => [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)



VMPLAYER is free and easy to install. Both Ubuntu and XP are running on the computer I am using right now.

---

### Post by Najand on 2006-09-16
> **tagra123 said:**
> VMPLAYER is free and easy to install. Both Ubuntu and XP are running on the computer I am using right now.

Well, you need at least VMWARE SERVER to install an OS that can be played by VMWARE PLAYER... The creators of VMWARE announced it free a few mounth ago, so feel free to install it... (Although I believe it is not an easy installation)

---

### Post by Ziox on 2006-09-16
> **Najand said:**
> Well, you need at least VMWARE SERVER to install an OS that can be played by VMWARE PLAYER... The creators of VMWARE announced it free a few mounth ago, so feel free to install it... (Although I believe it is not an easy installation)

With the HowTo I've provided, it is a very easy installation :biggrin:

---

### Post by tagra123 on 2006-09-16
Google for INSTALL VMPLAYER UBUNTU

Install VMPLAYER isnt hard 

HOW TO:
[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

You can install the VM Workstation (Trial) to create images program and create blank HDD images to install images to. The how-to shows a way that is more difficult. 

Install the player according to the how-to and then you should have everything to to install the Workstation.

XP will take a long time to install but it works very quickly once its installed. Be sure to install the VMWare tools too, it will allow better graphics and cut and pasting between Windows and Ubuntu.

Also once you get Windows installed to the virtual machine (make a backup or two) Come in handy later especially if something gets installed that breaks your windows installation.


If you have 8gb spare hard drive space I'd make the virtual drive as big as possible. XP is a hog once programs start getting installed.

---

### Post by Deonilin on 2006-09-17
ah ok kool sounds like the kinda thing i need. But does it require a fresh install of xp on the machine?

---

### Post by tagra123 on 2006-09-20
There are ways to access an existing copy on your harddrive, but I personally just do a new install on a virtual drive and of course reactivate it. I like th virtual drive because once its set up I can easily have the exact same machine on the laptop and desktop by copying the files over to the laptop. Install once copy to other machines -- windows has never asked me to reactivate either. 

By the way -- I installed the server now instead of the player. It has a lot more features including allowing you to create ne VMs the easy way (with the software instead of a lot of extra work)

It seems to run a little faster too.

The install will be extremely slow -- don't worry about it. Once its installed it will work very well. Remember to install vmtools ; the software will remind you to do that too.

---

### Post by Dr. C on 2006-09-20
It is also important to activate Win XP only after VMtools is installed.

---

