---
title: "Wireless PCMCIA help"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Damoedge on 2007-02-06
Hello

I'm a newbie to all this linux stuff and really wish I'd done a bit more homework. I decided to install unbuntu on my laptop as it's quite old and windows was slowing it down.

I've managed to install unbuntu and it's great but the only issue I have is my Linksys WPC54G V5 card.

Looking at the help stuff I'm guessing I need to use ndiswrapper, however I've never used Linux before so I was wondering if anyone could be a great help and provide a step by step instruction guide what to do it get the drivers installed. I have the original windows CD. Any help would be greatly appreciated.

Thanks

Damo

---

### Post by renzokuken on 2007-02-06
ok, here goes

get ndisrapper

```
sudo apt-get install ndiswrapper-utils
```

go onto your XP cd and copy the folder containing the drivers onto your desktop (the folder should contain .inf, .sys, and something else), run the following commands from the terminal

```
cd Desktop/nameoffolderwithdrivers
sudo ndiswrapper -i *.inf
ndiswrapper -l (this checks that it is installed)
sudo depmod -a
sudo ndiswrapper -m

```

you now need to get ndiswrapper to load at boot so,

```
sudo gedit /etc/modules
```

and add the following to the bottom of the file

```
ndiswrapper
```

---

### Post by Damoedge on 2007-02-06
not getting passed the second set of commands

home@home-laptop:~$ cd Desktop
home@home-laptop:~/Desktop$ cd Drivers
home@home-laptop:~/Desktop/Drivers$ sudo ndiswrapper -i *.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX

---

### Post by renzokuken on 2007-02-07
can you post the contents of your Drivers folder

```
cd Desktop/Drivers
ls

```

---

### Post by alexlindley on 2007-02-09
I'm also trying to install the WPC54g v5 and having so many problems.

I've read lots of people getting the v2 and v3 to work but no one with the v5, can anyone actually confirm they have one of these working?

I've tried installing with ndiswrapper but had no luck, the problem it has is that no power is given to the PCIMCA (or whatever its called on a laptop) card as the LED's dont light up.

This is even when ndiswrapper reports that the driver is installed correctly and the hardware is present!

Does anyone have any ideas? I've spent hours on this one.

Cheers,
Alex

PS. Damoedge, are you replacing the *.inf with the name of your driver, rather than just * ?

---

### Post by alexlindley on 2007-02-09
This is the thread to look at to get the WPC54g v5 working:
[http://ubuntuforums.org/showthread.php?t=355335&highlight=wpc54g](http://ubuntuforums.org/showthread.php?t=355335&highlight=wpc54g)

---

### Post by renzokuken on 2007-02-09
> **alexlindley said:**
> 
PS. Damoedge, are you replacing the *.inf with the name of your driver, rather than just * ?

i thought the * did it automatically like a wildcard. sorry, my bad. i sometimes struggle to explain things properly

---

