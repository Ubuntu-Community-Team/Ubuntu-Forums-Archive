---
title: "Bluetooth problems after upgrade to 11.10"
date: 2011-11-02
forum: Apple Hardware Users
---

### Post by eivindsm on 2011-11-02
Hi
I have a 27" iMac dual booted with OSX 12.2 and Ubuntu. The machine is equipped with bluetooth keyboard and mouse (no cables!). Under 11.04 my bluetooth hardware worked smoothly using the blueman bluetooth manger, but after upgrading to 11.10 I ran into problems. I`m still able to pair and trust the devices, but every time I boot into the other OS, the devices are not recognized, and I need to delete the stuff which is registered in the bluetooth manager and configure the devs from scratch. This is the case both ways, when I log on to OSX after ubuntu I need to re-register my devs, and the other way arround. To re-register the bluetooth devs I need a working mouse and keyboard, so its a catch 22. Login on to the machine is also a pain without a keyboard. 

I see plenty of other bluetooth issues reported after upgrading to 11.10, but not this one. I`m not sure if what I facing is an issue or a bug. 

Any ideas or workarounds?  Please!

---

### Post by Paul S on 2011-11-07
I have a more basic problem: Is there a way to get ubuntu 11.10 live cd to enable my imac (mid 2011) bluetooth keyboard and magic mouse and magic trackpad?

When I boot the live cd, the live cd enables the keyboard but not the mouse or trackpad in two places: 1) the language selection screen and 2) the "try or install" selection screen. Selecting "try" loads the desktop, but the devices fail to be enabled. They seem to be detected, because a popup window asks to enter a bluetooth security password. I tried entering the numbers, but the keystrokes don't show anything in the entry field. The popups just time out and disappear. This happens for the keyboard first, and then the magic mouse, but I didn't notice a popup for the magic trackpad.

After they disappear, I'm not able to do anything except use the power off to get out.

Then, I run into the problem you describe when I try to go back to OSX. The bluetooth devices don't get recognized by it, so I have to reboot  and remove the batteries multiple times before OSX will see them and pair. It's as though the linux kernel is changing the bluetooth chip somehow that OSX doesn't like.

---

### Post by zberger on 2011-11-09
> **eivindsm said:**
> I`m still able to pair and trust the devices, but every time I boot into the other OS, the devices are not recognized, and I need to delete the stuff which is registered in the bluetooth manager and configure the devs from scratch. This is the case both ways, when I log on to OSX after ubuntu I need to re-register my devs, and the other way arround. To re-register the bluetooth devs I need a working mouse and keyboard, so its a catch 22. Login on to the machine is also a pain without a keyboard. 


I'm having the same issue with Windows 7, OS X 10.7.2 and Ubuntu 11.10. Any solution yet?

---

### Post by eivindsm on 2011-11-13
This is most probably the same problem. Things worked so smoothly with 11.04 and now I have to pull out my ugly black USB keyboard to get in and out! Grr#!¤%

Does anyone have a solution? Would you guys describe this as a bug? To whom and where do you suggest that I report this issue?

---

### Post by matthew111 on 2011-11-23
> **eivindsm said:**
> Hi
I have a 27" iMac dual booted with OSX 12.2 and Ubuntu. The machine is equipped with bluetooth keyboard and mouse (no cables!). Under 11.04 my bluetooth hardware worked smoothly using the blueman bluetooth manger, but after upgrading to 11.10 I ran into problems. I`m still able to pair and trust the devices, but every time I boot into the other OS, the devices are not recognized, and I need to delete the stuff which is registered in the bluetooth manager and configure the devs from scratch. This is the case both ways, when I log on to OSX after ubuntu I need to re-register my devs, and the other way arround. To re-register the bluetooth devs I need a working mouse and keyboard, so its a catch 22. Login on to the machine is also a pain without a keyboard. 

I see plenty of other bluetooth issues reported after upgrading to 11.10, but not this one. I`m not sure if what I facing is an issue or a bug. 

Any ideas or workarounds?  Please!

I am having the same issue with a 21.5" iMac with a slight variant in that in 11.10 it is difficult to pair the keyboard and mouse. The keyboard and mouse are only found sporadically. I am able to get them paired eventually, but it takes multiple attempts of adding/deleting the devices.

Any help would be great!

---

### Post by eivindsm on 2011-12-17
Dear forum! 

Does anyone have a solution for these bluetooth issues?

---

### Post by bford16 on 2011-12-17
Sorry,

No solution; just chiming in to say that I, too, am having problems with bluetooth that I did not have before.  I am using a bluetooth dongle. I have Plantronics BB903+ headphones. I can pair them with the dongle. When I go to Sound Preferences, I have to select the Bluetooth hardware and set it to A2DP, then switch to Output and choose the WRONG hardware.  This causes the headset to appear as an option, and it works perfectly when I select it.

BUT!! If I disconnect the headphones, then I cannot re-connect.  I have to delete the device, and go through the whole process again...

Is there a bug for this?

---

### Post by pbhedlund on 2012-05-16
> **eivindsm said:**
> Dear forum! 

Does anyone have a solution for these bluetooth issues?

No progress in 12.04 either. I started a new thread ([http://ubuntuforums.org/showthread.php?t=1980171](http://ubuntuforums.org/showthread.php?t=1980171)) because i hadn't found this one.

---

### Post by onze11 on 2012-05-16
Bonjour, 
problème de batterie , vous pouvez consulter le site :
[http://www.pcbatterie.com/](http://www.pcbatterie.com/)

---

### Post by pbhedlund on 2012-05-20
Bug report [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825).

---

### Post by eivindsm on 2012-05-21
Thanks for filing the bug! I should have done it myself, but I never got around to do it.

---

