---
title: "no video"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by amer1337 on 2007-10-09
i installed ubuntu 7.04 on both my desktop and laptop, with nvidia 6800 and gf go 6100, neither boot up the live cd visible unless i trll it what video mode to start up with. 

but when i install ubuntu to the harddrive it installs fine, but when i boot up it goes to a black screen. how do i get the desktop to show?

---

### Post by Pumalite on 2007-10-09
Ctrl+Alt+F1 to get a command line, then:

sudo dpkg-reconfigure xserver-xorg, accept defaults, choose 'vesa' as the driver, then: startx

---

### Post by amer1337 on 2007-10-10
awesome, thank you :)

edit : when i hit ctrl alt f1 nothing happens

---

### Post by amer1337 on 2007-10-10
bump, anyone? im reinstalling with kubuntu but the same thing keeps happening, just gives me a black screen right before the gui should start loading, and xtrl alt f1 doesnt bring a thing up.

---

### Post by overdrank on 2007-10-10
> **amer1337 said:**
> bump, anyone? i tried reinstalling with kubuntu and the same thing happens, just gives me a black screen right before the gui should start loading, and xtrl alt f1 doesnt bring a thing up.

Ok so you do see the grub loading and then black screen correct?
You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add vga=771 and then hit enter and then  b to boot. Hope this helps. Good luck!

---

### Post by amer1337 on 2007-10-10
well i get an ubuntu load bar, and once it completes then the black screen, ill try what you suggested right now
edit:: nope didnt do anything, it doesnt seem to be saving it either becuase after it hits the black screen and i reboot, it still has "quiet" instead of vga=771

---

### Post by amer1337 on 2007-10-10
i started in repair mode or watever and it says no screens found when i try to connect to startx, but half the time the boot in the repairmode just freezes and sits for > 10 minutes and im forced to hard reboot it

---

### Post by amer1337 on 2007-10-10
any ideas or should i just go reformat to debian or another distro?

---

### Post by amer1337 on 2007-10-11
bump, desperate :)

---

### Post by Pumalite on 2007-10-11
Post your specs. You might need Alternate CD or lighter Desktop. Also keep in mind this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by handydan918 on 2007-10-11
When the GRUB menu comes up, immediately press ESC.
Press 'e' and you can add vga=771 to the end of the GRUB line.
Then press 'b' to boot.
If this doesn't work, try booting into repair mode and do 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by amer1337 on 2007-10-11
exactly where do i add vga=771 in grub, cause i added it as a line and it just disappeared when i booted up next

amd x2 turon tk-55, 1gb of ram, 120gb sata hard drive, gf go 6100, not sure about the mainboard, its a compaq presario 730us

ive burned probably 10 different cd's total, redownloaded the iso's for both ubuntu and kubuntu

EDIT :: THANK YOU, i was adding vga=771 on its own line and not on the kernel line, it boots up now, but how can i fix this? do i need to isntall nvidia drivers ?

---

### Post by Pumalite on 2007-10-11
In case you have an nvidia card:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

This also:

'If you want to install nVidia for your graphic card, just do System -> Administration -> Restricted Drivers Manager -> Enabled. No need to download and install it by hand.'

(thanks to taurus)

---

