---
title: "Ubuntu Installation"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by joshbanter on 2008-02-16
Well I installed Ubuntu 3 times on my computer the past week and somehow it seems Ubuntu is configured differently each time. I mean in terms of mouse/keyboard setting, hardware detection and such. 

And so the very first time I installed ubuntu, the only problem I had was to configure my logitech mouse and keyboard combo. It wasn't a big deal. I did abit of research and most buttons worked alright except the up/down scroll button (not the wheel). Most hardware seemed to work fine - sound card, graphic card, etc works except for my old wintv usb card.

The second time I installed, it was on the same machine but another hard drive. My mouse and keyboard buttons worked from the start. Even my up/down scroll button worked. I didn't try my tv card but everything else worked.

Now, for my third time, I installed back to the original drive and still on the same machine. My mouse and keyboard buttons aren't working without configuration. Also, Ubuntu doesn't detect my creative audigy 2. For the first 2 installation both my onboard and pci sound card were detected and I was able to use both. This time around, only my onboard is detected.

So my question is why the installation result varies with each installation? I didn't recall doing anything different on each installation. Each was installed with Ubuntu 7.10 LiveCD by the way.

Oh and how do I make ubuntu detect my sound card now that it's not detected?

Thanks for reading and please hit the reply button :lolflag:

---

### Post by njparton on 2008-02-16
Is there some other problem that's forcing you to reinstall each time or do you just *enjoy* the process?

---

### Post by fatality_uk on 2008-02-16
> **njparton said:**
> Is there some other problem that's forcing you to reinstall each time or do you just *enjoy* the process?

+1
You stated that after install 1, everything worked pretty much fine. Other than to prove a point, why install over and over again?

If you type lspci into a terminal and post the output here

---

### Post by joshbanter on 2008-02-18
Hahaha...  as exciting as trying ubuntu can be, I wouldn't install it over and over again for the sake of it. I don't think I have such fetish...... :lolflag: 

It all began when I needed to reinstall XP because it  suddenly went so slowly after installing ubuntu. I tried to install XP again, the installer wouldn't let me. It has something to with the number of non-logical partition on the same drive. So I decided to just wipe the HD clean since I haven't done anything much in ubuntu anyway. I didn't install ubuntu back on the HD after installing XP. 

The second time around, I was installing it on a spare HD. I was wondering if I could install ubuntu on my machine and then fix it on another older machine. Now I know it doesn't work. But this particular installation had everything set right, at least from my perspective. But since it's not my HD to begin with, I decided to install ubuntu on my own HD. And so I came to the third installation which doesn't end up as well as I hope it would. 

My concern is just why it produces different result each time? Maybe if I know what's causing it, I'll avoid next time I need to install ubuntu again for whatever reason may that be.

I did lspci and there was only one multimedia controller detected, it was my AC'97 on board audio. I tried to disable it and see if my creative sound card would be detected but no avail.  But I'll post my LSPCI once I boot back into ubuntu.

EDIT: Added lspci
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:03.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

```

---

