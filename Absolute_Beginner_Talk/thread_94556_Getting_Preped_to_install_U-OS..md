---
title: "Getting Preped to install U-OS."
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by amwil1024 on 2005-11-24
Soon, I will format my hardrive, reinstall Win98SE with a minimum of software. 12g harddrive, 450mhz intel PIII, 512k RAM. I will do a dual os using ubuntu.

1. I have photographs on Win98SE that I took with my digcam and MS-Word documents. I burned them to a cd. Will I be able to transfer them to U-OS?

2. When I install U-OS, will "it" partition the hardrive? If so, Can I set partition size? Should I partition HD ahead of time when I format it? I want at least 50% to go to U-OS, if not more.

3. I know already that I must obtain linux modem driver for dial up / hcf modem, but, I'm getting cable modem installed Dec. 8th, what issues are there in running linux on cable modem?

Processor: Intel Family 6 Model 7 449 Mhz Stepping 2
Math Support: On chip
BIOS: Phoenix Tech.s 04/22/99

---

### Post by SuperMike on 2005-11-24
[QUOTE=amwil1024]Soon, I will format my hardrive, reinstall Win98SE with a minimum of software. 12g harddrive, 450mhz intel PIII, 512k RAM. I will do a dual os using ubuntu.

1. I have photographs on Win98SE that I took with my digcam and MS-Word documents. I burned them to a cd. Will I be able to transfer them to U-OS?

2. When I install U-OS, will "it" partition the hardrive? If so, Can I set partition size? Should I partition HD ahead of time when I format it? I want at least 50% to go to U-OS, if not more.

3. I know already that I must obtain linux modem driver for dial up / hcf modem, but, I'm getting cable modem installed Dec. 8th, what issues are there in running linux on cable modem?

Processor: Intel Family 6 Model 7 449 Mhz Stepping 2
Math Support: On chip
BIOS: Phoenix Tech.s 04/22/99[/QUOTE]

Congratulations on joining the ranks of people who abandon Winders to go with something more stable, forward-thinking, and useful.

1. Sure, you bet! Just stick in the CDR and it appears on your Ubuntu desktop. Doubleclick it and drag the files out. The images, no matter which format you created them in, will open just fine if you doubleclick them. The Word Docs will open in about 85% compatibility in OpenOffice.org 2.0 beta 2, which comes with Ubuntu. Or, if you are clever enough and get enough online help, you might learn how to enable Xen or Wine and open your Word Docs natively in MS Office.

2. Relax. Let Ubuntu do it's thing. When you see that you are prompted on how you want to partition the OS, they have an easy option that's pretty straight-forward, or an expert option. In your case, I would normally avoid the expert option, but unfortunately it appears you want something that I think you can only achieve in the expert option. So, be careful. Also, please understand that even when you want 50% of disk for Linux, you must be careful to understand that you must give it space for rootdir (/), swap space (/swap), and boot (/boot). So you have to make 3 partitions in that remaining 50% you have provided for Linux. You can let Ubuntu's installer automatically assume the sizes of these partitions (rootdir, swap, and boot) -- it's smart, I think I recall -- or you can create swap as 2x RAM size + 2MB (to be safe) and then create /boot with 15MB (to be REALLY safe -- that should be MORE than enough room), and then finally leave the rest to rootdir with all the rest of the available space.

3. You know, with cable modems, I recommend that instead of plugging it directly into your Linux, I recommend you go out and purchase what's known as a DSL/Cable Modem Router. These are fairly cheap, come with a firewall, and are fairly effective in helping you set up your cable modem faster and in helping you protect your systems a little better. (Although, nothing's perfectly going to keep you 100% secure on any OS.) They are also fairly easy to setup with a large color brochure. Then, when you start to build up your "iptables" skills, you can learn the proper iptables statements you can have in a boot script on your PC to lock it down even more. At my house, I have 2 firewalls -- the Router has one and then my PC has one. That way, if my kids infect one of the other PCs behind the router, I won't get my Linux PC turned into a zombie virus PC.

BTW, some other cool things to try on Linux:

* rdesktop and tsclient -- gives you a way to connect to other PCs at home or in the office via Microsoft Terminal Services or Real VNC.

* 3ddesktop (have to enable "Universe" mode temporarily in your /etc/apt/sources.list in order to install, then comment the "Universe" mode option out to keep your system safe). With 3ddesktop, you can flip between workspaces in this WICKED 3D mode. You have to do man 3ddesktop to see how it works.

* Screem, if you like doing programming

* InkScape -- if you like doing cool graphics.

BTW, something to warn you about with Ubuntu:

* People may recommend that you add things to your /etc/apt/sources.list file. This comes with some risk, so do so at your own peril.

* Sometimes I do dip into the "Universe" waters of /etc/apt/sources.list to install extra stuff from Synaptic that normally isn't there, and I'm aware that this isn't fully tested or supported by Canonical. However, after doing that, I NEVER update my system when prompted with the little red icon on the bottom right-hand corner of the screen because that would cause my PC to download EVEN MORE beta stuff. Once I have installed my item from the Universe option, I comment it back out, update my Synaptic (or use apt-get update), and then log out and back in again. If my little red icon on the bottom right-hand corner of the screen comes back on again in this condition, I **DO** let it update my system. And why? Because with the Universe option turned off, it is fairly safe to have your system get updated when prompted.

---

### Post by jorn on 2005-11-24
To 1. I should be very surprised if you doesn't.
    2. Defrag win98 before installing Ubuntu. That will give you more free space.
       You will be able to set partition size while installing.
    3. Adsl worked out of the box for me.
Jorn

---

### Post by 23meg on 2005-11-24
[QUOTE=SuperMike](have to enable "Universe" mode temporarily in your /etc/apt/sources.list in order to install, then comment the "Universe" mode option out to keep your system safe)
[/QUOTE]
[quote=SuperMike]
* Sometimes I do dip into the "Universe" waters of /etc/apt/sources.list to install extra stuff from Synaptic that normally isn't there, and I'm aware that this isn't fully tested or supported by Canonical. However, after doing that, I NEVER update my system when prompted with the little red icon on the bottom right-hand corner of the screen because that would cause my PC to download EVEN MORE beta stuff. Once I have installed my item from the Universe option, I comment it back out, update my Synaptic (or use apt-get update), and then log out and back in again. If my little red icon on the bottom right-hand corner of the screen comes back on again in this condition, I **DO** let it update my system. And why? Because with the Universe option turned off, it is fairly safe to have your system get updated when prompted.[/quote]This isn't completely true. You don't have to worry about updates to Universe packages, simply because they don't happen except for development releases. Ubuntu does not provide any updates except security ones after releases, to increase stability. Furthermore, even security updates aren't guaranteed for Universe.

---

