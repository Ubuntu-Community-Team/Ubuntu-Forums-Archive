---
title: "Skype not connecting"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by latham1982 on 2005-10-27
hi folkes
new to linux and slowly wading through teething problems
my latest is skype installed as explained on [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)
but no joy the program starts fine but doesn't connect - Logging in failed.
my mozilla is working fine as is synaptic but I tried to run the automatix program and that didn't work it couldn't locate the respositories that synaptic can,
any hints, solutions, directions?
many thanks
john
ps been thinking about the problem a bit more synaptic and firefox both have the proxy entered with the program configs
At skype.com it says the skype gets proxy info from opera configs. I don't run opera so where does it get the proxy from?
Is there somewhere where I can enter a "system proxy config" or something like that?

---

### Post by Ampersand on 2005-10-27
You can fill in your proxy settings by going to System - Preferences - Network Proxy (in the menus at the top of the screen, if you haven't altered the panels).

---

### Post by latham1982 on 2005-10-28
Felt quite silly when you pointed this out but tried it and still no joy skype just sits there saying that it is connecting but does nothing. wish I could give more info but don't know what other info could be useful.

---

### Post by Ampersand on 2005-10-28
Have you tried:
```
export "http_proxy"="host:port" 
```
or something similar? (the other bit in the skype faq about it)

Also, are you running the latest version of Skype?

---

### Post by Liz on 2005-10-29
hi all, 

i got skype working, i can hear the other person in skype even, but for some reason, my mic (brand new, just bought it ) isnt working. it wont work in gnome recorder program, wont work in skype, YET works in windows when i plugged it in there. 
checked that i have the cords in teh right place, followed the troubleshooting page from the link in the troubleshooting page..still no mic. 

any help would be appreciated. 
here is my output from lspci 
" lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

again, any help would be great. 

thanks

---

### Post by latham1982 on 2005-10-29
still no joy the program just sits there going to try installing opera to see if this helps any suggestions. (Skype is latest version)

---

### Post by Ampersand on 2005-10-29
[QUOTE=Liz]hi all, 

i got skype working, i can hear the other person in skype even, but for some reason, my mic (brand new, just bought it ) isnt working. it wont work in gnome recorder program, wont work in skype, YET works in windows when i plugged it in there. 
checked that i have the cords in teh right place, followed the troubleshooting page from the link in the troubleshooting page..still no mic. 

any help would be appreciated. 
here is my output from lspci 
" lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

again, any help would be great. 

thanks[/QUOTE]

Just to check, have you made sure the relavent inputs are unmuted and enabled in the volume control (sound and video menu)?

---

### Post by Liz on 2005-10-29
[QUOTE=Ampersand]Just to check, have you made sure the relavent inputs are unmuted and enabled in the volume control (sound and video menu)?[/QUOTE]


yep, checked that one too. was the first thing i did. 
i get sound just no mic noises. 
closest ive gotten is hash noise after recording (gnome record program)

cheers.

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

