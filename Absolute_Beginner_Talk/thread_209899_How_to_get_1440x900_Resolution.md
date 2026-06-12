---
title: "How to get 1440x900 Resolution"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2006-07-05
Hi,

I've got a Widescreen LCD and the maximum resolution ubuntu will let me run at is 1024x768 (I run at 1440x900 in Windows).
As I'm running ubuntu as a Virtual Machine inside VMWare Player (which is now free, and I downloaded the Virtual Machine from VMWare too so it's the standard setup used by many I would expect (available [here.]("http://www.vmware.com/vmtn/appliances/directory/484")) maybe someone else has had the same problem? I've checked these forums and the VMWare Support Forums too, and I'm going to add a post there - I reckon you'll have equal chance of knowing here since this is could be a ubuntu and/or VMWare issue (I'm not going to point fingers!).

Thanks very much, all your input is very much appreciated!

EDIT: I've posted this same question on the VMWare forums, [here.]("http://www.vmware.com/community/thread.jspa?threadID=47244")

---

### Post by K.Mandla on 2006-07-05
This is a shot in the dark, but have you edited your /etc/X11/xorg.conf file to allow 1440x900? I'm guessing you tried that already.

---

### Post by catlett on 2006-07-05
I don't know much about vmware but I am assuming you can reconfigure the vmware install. If you can this is how you reconfigure  x . ```
sudo dpkg-reconfigure xserver-xorg
``` This takes you through the setup of X. The more info you enter the better, It will ask about your video card, monitor, keyboard etc. It can auto detect but it is always better to enter the info manually. Go to your video card and monitor's web site and get the specs on both. This way you can enter max resolution, horizontal and vertical refresh rate, etc.
One thing I do is selct all possible resolutions. The page before the resolution setting givers you a prompt like this "checking all the resolutions or not checking any resolutions will cause the setup to list all available settings" Otherwise it will only list what you chose. I check them all off so I get all possible resolutions.
Hopefully it will work on a vmware install. I would assume the default vmware machine is very "neutral" to make it as compatible as possible to the most systems. I would almost bet it is running the vesa driver. Running the reconfiguration will result in a better driver for your system being installed, if it works on vmware.

---

### Post by srunni on 2006-07-05
I tried to do this a while ago, and ended up totally screwing up my xorg.conf file. When I restarted Ubuntu, I saw command line, and had to restore the xorg.conf to its original state using an xorg.conf_backup file that I happened to have.

---

### Post by Thenotsowyzewun on 2006-07-06
I haven't tried reconfiguring the xorg.conf file, this is what they recommended on the VMTN forums too so I'm gonna try that, good luck me! Course I'll report back on how well I do...

[QUOTE=srunni]I tried to do this a while ago, and ended up totally screwing up my xorg.conf file. When I restarted Ubuntu, I saw command line, and had to restore the xorg.conf to its original state using an xorg.conf_backup file that I happened to have.[/QUOTE]

Lucky it's just a virtual machine then (if I screw it up I'll just "forget" to save the state when I close VMWare ;).

EDIT: Didn't work :(, thanks for trying though.
Not that I'm gonna give up that easily! Just don't know what to try next...

---

### Post by PingunZ on 2006-07-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and select the resolution you want by pressing* Space * and then * Enter *
then ctrl + alt+ backspace and type * startx *

---

### Post by Thenotsowyzewun on 2006-07-06
[QUOTE=PingunZ]```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and select the resolution you want by pressing* Space * and then * Enter *
then ctrl + alt+ backspace and type * startx *[/QUOTE]

Excellent :KS that worked perfectly (to the point that I logged back in and it took a second for me to clock that the black bars were gone hehe).

---

### Post by catlett on 2006-07-06
[QUOTE=PingunZ]```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and select the resolution you want by pressing* Space * and then * Enter *
then ctrl + alt+ backspace and type * startx *[/QUOTE]
That's a great one pingunz, I never knew about that option. You're a wealth of good info. I followeed your sig link and ended up at your gfxboot. Very nice.:D

---

