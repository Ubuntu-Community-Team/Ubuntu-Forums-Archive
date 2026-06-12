---
title: "Grub bootloader troubles 7.10"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Lok5 on 2007-12-06
Alright first off I am a total noob to linux but not computers as I have been working with computers and building my own PCs since I was 8 back when MS dos was all you had to install and launch Doom. :P

With that said I have partitioned and installed ubuntu 7.10 on my DV9009nr laptop with no trouble. But the only way I could get the livecd to run is with quiet turned to noapic and noddc res=1440x900 opengl=nvidia. So now when I start it up grub loads perfectly and gives me the option to pick what I want and I try to start ubuntu but it stops at like 20%. 

I have gone into the grub bootloader options and tried to make my own boot options but everytime I say boot it restarts and starts over with the old boot options. Is there any way to save my own boot options that I am not aware about? The list of commands says nothing about save setting so I'm pretty much stuck at this point. 

I  have several other distros I would like to try as well but I figure if I cant even get this to run how am I ever going to get Sabayon up and running on my system. 

I dual boot with XP media center edition that I went back to cuz vista is balls! The only reason I even use it is because I am an audio engineer and I have to use windows for Nuendo 4 to run on and for my firewire audio hardware. I hate windows too so please don't give me crap about it.

Any help anyone could give me would be GREATLY appreciated as I still need to get KDE and compiz fusion up and running on it too. Along with firefox64 bit edition......lots of work to do still. Need to get this first step out of the way.

Thanks
Lok5

---

### Post by ajmorris on 2007-12-06
From the grub boot settings at boot, the settings can not be changed. However, if the boot options work, and you can boot into ubuntu, once you're in, you can edit, /boot/grub/menu.lst and change the settings in there, save the file, and the settings will stay like that always.

---

### Post by Lok5 on 2007-12-10
I can't get it to boot up though. When I go into grub boot options I put it what I want to boot with and select BOOT and it restarts and the old boot setting are put back in place when grub starts up again.

Is there something really easy I'm missing here?

-Lok5

---

