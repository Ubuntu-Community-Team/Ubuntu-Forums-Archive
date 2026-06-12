---
title: "getting online"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Suse on 2007-11-16
Hi

I apologise if this has been raised before, but i can't quite see what I'm looking for. I don't know how to set up my internet connection. Have just set up 6.06 on Microsoft Virtual PC (host PC is XP Home). I'm using 6.06 cos I just couldn't get 7.10 to install. I am using a D-Link DSL-2640B wireless router and D-Link DWA-111 wireless card.

The reason I'm using Ubuntu is that I want to see if Linux is for me. I'm using it on Virtual PC instead of creating a dual boot because I'd might decide to run my main applications on the host PC but the internet on Ubuntu, so I can go online in a safer environment. I'm no computer whiz, and perhaps with Ubuntu I'm trying to go beyond what the technical side of my brain is capable off, as usual!

I had an initial start up problem logging in where the keys were going too fast (ie, I had to tap the keys gently so they wouldn't multiply). Was ok after resetting. Next I also got a message about 'HAL' something or other. I reset it again and that disappeared, but then there were no icons on the screen. However, after 4th reset no errors and everything seems fine:-D

Any help much appreciated.

---

### Post by Suse on 2007-11-16
Further to my post above. I've tried following the guide for getting Ubuntu to recognise my wireless card (it's not one of the specific ones listed). I get as far as this part:


      If you get no output then the memory on the card cannot be read.

      Now we need to open a configuration file and add this information to it:

        gksudo gedit /etc/pcmcia/config.opts
        

      the information you add should look like this, with your own data substituted.

IconExample48.png

    *

      card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
        manfid 0x0271, 0x0012
        function: 6 (network)
        bind "ath_pci"
        

Problem is, how can I find that information???!

---

### Post by mellowd on 2007-11-16
I haven't used virtual pc unfortuantely. I have used vmware though and with vmware you can 'share' the network card with the host pc. As Windows is currently running it essentially controls the wireless card so you would need to ensure ubuntu is speaking to the host pc, not directly to the wireless card. The host pc will then essentially route traffic through to the internet and back

---

