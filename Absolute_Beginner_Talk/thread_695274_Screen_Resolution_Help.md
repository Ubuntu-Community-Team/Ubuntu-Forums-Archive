---
title: "Screen Resolution Help"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by glenb83 on 2008-02-12
Hi all,
I have a HP Compaq nx9110 laptop with Ubuntu Gutsy installed. The highest resolution I can get on it is 1024x768. I was wanting to know if I can get it at a higher resolution? When I go into hardware information, it lists the video card as RS300M on Radeon 9100 IGP AGP bridge. When I go into screens, the device is listed as ATI - Mach and Rage varieties, however whenever I change this, it automatically goes back to this driver. 

Has anyone got any suggestions how I can increase the resolution? I only want to go up one more, to be able to view websites etc a little easier.

Thanks

---

### Post by Rocket2DMn on 2008-02-12
If you can't select the correct resolutions from System->Preferences->Screen Resolution, you will probably need to reconfigure X, it's pretty straightforward.  Let's start with the auto-detect method:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```  Then restart X with CTRL+ALT+BACKSPACE (make sure everything is saved and closed since this will restart your GUI).  
If you still can't select your resolution, follow this guide to manually reconfigure - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by dcstar on 2008-02-12
> **glenb83 said:**
> Hi all,
I have a HP Compaq nx9110 laptop with Ubuntu Gutsy installed. The highest resolution I can get on it is 1024x768. I was wanting to know if I can get it at a higher resolution? When I go into hardware information, it lists the video card as RS300M on Radeon 9100 IGP AGP bridge. When I go into screens, the device is listed as ATI - Mach and Rage varieties, however whenever I change this, it automatically goes back to this driver. 

Has anyone got any suggestions how I can increase the resolution? I only want to go up one more, to be able to view websites etc a little easier.

Thanks

CTRL-ALT-F1, log in as normal, then:
```
sudo dkpg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```
The choices are usually left at defaults, and you can run it again if you need to.

---

### Post by oedha on 2008-02-12
when i still had problem after done like what dcstar and rocket2dmn advices....i'll change the resolution manually in /etc/X11/xorg.conf

---

