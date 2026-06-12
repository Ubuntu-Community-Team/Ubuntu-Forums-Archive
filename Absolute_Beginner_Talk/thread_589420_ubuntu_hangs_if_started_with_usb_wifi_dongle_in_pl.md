---
title: "ubuntu hangs if started with usb wifi dongle in place"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by linyanam on 2007-10-24
Hi 
I am a complete noob.
After upgrading to gutsy the computer hangs if booted with usb dogle in place. It has rt73 chipset BN-WD54G (bleunext usb wifi dongle). The problem was there with upgrade and is there with fresh install. Worked fine in Feisty but I had different problem then so I decided to upgrade.
The network manager was not working reliably  so I used Ndiswrapper and subsequrently Serial monkey drivers. Ubuntu connects but the hanging problem was still there with either methods.
Currently I think both drivers are still in use, as   at different times  "lshw -C network" command shows wireless=RT73 WLAN at some times and Ndiswrapper-rt73 at other times (after reboots or after starting from hibernation.)
Currently I insert the dongle after Ubuntu fully loaded and use "sudo dhclient wlan0" command and use rutilt to connect my WAP wireless network.
But I have to remove dongle each time I shutdown or hibernate.
What can I do to fix this.
How do I record the error messages with hanging. I restart with Ctrl SysRq reisub command after yanking the dongle.
Cheers,
Linyanam.

---

### Post by cameronol on 2007-10-26
I'm having the same problem, what i did is just take it out then put it back in when Ubuntu starts after the login screen. It then worked perfectly

---

### Post by RKCole on 2007-10-26
I had this problem in the past.  I used the SerialMonkey drivers to get it up and running properly, but Ubuntu apparently loads multiple drivers at once for this device by default.  What I did to solve this problem was to blacklist each of the drivers so that they would not load at startup.  Here is the procedure I followed:

Open the file **/etc/modprobe.d/blacklist** in your text editor of choice (with root privileges).  In my case this was Gedit.  To do this quickly, simply hit ALT+F2 to open the **Run Application** dialog box and enter:

```

gksudo gedit /etc/modprobe.d/blacklist

```

Add these lines to the end of the blacklist file:

```

#Blacklisted RT-based wireless drivers
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib

```

Save the file.

That solved my problem immediately for me.

Hope this helped.

Take care.

---

### Post by linyanam on 2007-10-27
Hi,
I already blacklisted all of them and yes I am currently using my system by inserting usb dongle after login screen. I have not tried rebooting with dongle in place as I do not want to have new  problems.
I cant connect automatically to the WPA router. The CLI instructions at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) did not work for me.
I use rutilt to connect, it does not connect automatically even if I saved the profile. It connects to router but with out ip address. I have to scan again and connect by entering password each time. A small trouble which I am prepared to put up with.
Thanks for your help.

---

