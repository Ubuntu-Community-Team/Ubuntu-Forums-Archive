---
title: "Switching primary graphic adapters"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by i3ear on 2008-01-20
I am switching from my onboard shitty SiS-something video adapter to a 3dfx-something AGP card

I plugged it in, Ubuntu installed the driver (I think) when I booted it for the first time with this card in (It went to terminal mode and downloaded something)

So I started it up, and I get nothing from the card. So, what am I doing wrong?

---

### Post by jleaker01z on 2008-01-20
You might need to disable the onboard video from within your system BIOS.

---

### Post by i3ear on 2008-01-20
Any chance that I will be stuck without video? (and therefor stuck having to reset the BIOS)

---

### Post by i3ear on 2008-01-20
> **jleaker01z said:**
> You might need to disable the onboard video from within your system BIOS.

Tried that

Can't switch off my integrated video.

---

### Post by jleaker01z on 2008-01-20
Wow...ok that is odd.  Did you try to hook the monitor up to the onboard video port to see if that is giving an output?  Most motherboards will disable the onboard automatically when it detects an addon card has been installed, but you would be surprised at how often I have seen that not happen.

---

### Post by i3ear on 2008-01-20
My MB is extremely werd, its a Foxxconn that came with a Systemax PC, with the BIOS written by AOL or something (no srsly, the splash screen says that)

But yeah, I tried that, nothing.
I was thinking a multi-screen program or addon that I could use, than disable my onboard and enable my card.

---

### Post by jleaker01z on 2008-01-20
Open a terminal then copy and paste the following line:
eh wait one...

---

### Post by i3ear on 2008-01-20
*****@*****:~$ lspci | grep -i pci || lspci
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
******@*****:~$

If you don't mind my useless paranoia. :P

---

### Post by jleaker01z on 2008-01-20
deleted

---

### Post by jleaker01z on 2008-01-20
> **i3ear said:**
> *****@*****:~$ lspci | grep -i pci || lspci
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
******@*****:~$

If you don't mind my useless paranoia. :P

It looks like Ubuntu is trying to use the SIS onboard video.  It really needs to be disabled and I dont understand why there is not an option somewhere within your bios to disable it.

(If it was disabled automatically by the mainboard it shouldnt even show up...)

---

### Post by i3ear on 2008-01-20
Like I said, my BIOS is werid, maybe I should look for updates for it?

Is there any way to get Ubuntu to recognize it and use it?

---

### Post by jleaker01z on 2008-01-20
You can try a BIOS update.  Ubuntu will only see what the motherboard/bios says is there.  Thats normal for any OS.  It is obviously some type of hardware issue tho.

---

### Post by i3ear on 2008-01-20
Can't update the BIOS, the exe that is there to make a floppy to update the BIOS will not work with Wine

Or if it does then I don't know how to use wine (right clicking and hitting "Open with Wine"

---

### Post by jleaker01z on 2008-01-20
I'm afraid I'm at a loss, other than the old standby like:

[IMG]http://img401.imageshack.us/img401/5681/levjpgxj0.gif[/IMG]
This is how we fix things on Russian space station!!!

---

### Post by i3ear on 2008-01-20
Hahahaha YES
RUUUHSHIN AMERICKKAN
ALL MADE IN TIWAN

But blah, how do you run WINE in terminal?
I am quite the linux n00b so help me out here.

---

### Post by jleaker01z on 2008-01-20
Just enter wine blahblah.exe in the directory your exe file is located.

---

### Post by i3ear on 2008-01-20
Nope, need libraries

****, whell I am ****** for a while untill I can get access to my moms computer (that has XP on it)

Thanks alot!

---

### Post by daengbo on 2008-01-20
i3ear,

Did you reconfigure xorg.conf to use the new video card? If not, remove the new card boot into the old sis900 chip )man that one sucks!), and reconfigure Screens and Graphics to use the Vesa driver. Then you can shutdown, put in the new card, attach it to the monitor, and boot up. Once in vesa mode, you can reconfigure Scrrens and Graphics to use the driver for the new card.

---

### Post by i3ear on 2008-01-20
Alright, did that

Didn't work.

---

