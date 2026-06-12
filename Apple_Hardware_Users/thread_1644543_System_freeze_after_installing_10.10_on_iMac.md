---
title: "System freeze after installing 10.10 on iMac"
date: 2010-12-13
forum: Apple Hardware Users
---

### Post by Old Codger on 2010-12-13
I successfully installed Ubuntu 10.04 Lucid on my relatively new iMac 21.5 10,1, but have been unsuccessful in running the upgrade to 10.10 Maverick Meerkat in the normal mode. It appears that the system freezes and/or does not recognize input from either the wireless mouse (aka magic mouse) or keyboard. However, I am able to boot in the recovery/failsafe mode. :confused:

I previously attempted to install from a live CD, etc., but the same thing happens, regardless of the type of install I've tried.

Has anyone who has had the same problem found a fix to boot in the normal mode?

Thanks in advance

---

### Post by ZeroLinux on 2010-12-13
I recently installed on my iMac 21.5 Ubuntu 10.10
System does not freeze. But I use USB mouse and keyboard...

---

### Post by Old Codger on 2010-12-14
I've heard that 10.10 will work if you use a usb mouse and keyboard, but I was hoping that someone had found a fix for the wireless versions. :cool:

---

### Post by arabis on 2010-12-14
[http://ubuntuforums.org/showthread.php?t=1639129]("http://ubuntuforums.org/showthread.php?t=1639129")

---

### Post by Old Codger on 2010-12-15
Arabis, I've tried the recommended fix on the link. It didn't work for me. What puzzles me is that the keyboard and mouse worked in a limited way when I ran 10.04 in normal mode. I don't understand why I can't log-in the normal mode in 10.10. :confused:

---

### Post by albasnians on 2010-12-15
I am also facing same problem from a long time and tried many thing but still cant figure out the solution. Still searching hope I will make it soon.

---

### Post by arabis on 2010-12-15
When you are in recovery mode the bluetooth mouse and keyboard work with limitations, but in normal mode you have to pair them once with blueman to make them work. In normal mode you can use a regular mouse before you succeed to pair your magic mouse (code 0000). To pair your keyboard, use a virtual one (it is called "onboard") to write 1234 when blueman ask for code, and answer back with your bluetooth keyboard. Just make sure you make a shortcut on your desktop for "onboard" before, when you are in recovery mode.

Also, make sure you use blueman to pair your devices and not the default bluetooth manager. It may take many tries before you succeed to pair your device. Don't give up, try many times. Once you have paired successfully your devices, when you login again, you have to trigger your mouse by clicking once and your keyboard by hitting a key. Wait for the little green light on the keyboard before you enter your password.

---

### Post by Old Codger on 2011-01-03
Thanks, Arabis, but I've decided to revert to a wired keyboard and mouse in this case.

---

