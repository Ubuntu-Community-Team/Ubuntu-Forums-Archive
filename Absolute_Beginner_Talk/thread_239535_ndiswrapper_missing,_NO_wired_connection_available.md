---
title: "ndiswrapper missing, NO wired connection available"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by random.brown on 2006-08-19
Hello,

I'm trying to set up my wireless PCI card (broadcom drivers), but when I try to enter *ndiswrapper* commands it tells me that the ndiswrapper command isn't found.

I thought it was installed with base install of 6.06.1?

Also, all the instructions I can find for setting up wireless cards with broadcom chipsets start with "we assume you have a wired connection to the internet..."

I don't.  I dual-boot to my windowsxp install to get online, since my PCI card is auto-detected by windows...

Is Ndiswrapper installed, but just not in the "path?"  If not, can I download it from windows and install it from my fat32 drive?

Any help is appreciated!

---

### Post by TFX360 on 2006-08-19
> **random.brown said:**
> Hello,

I'm trying to set up my wireless PCI card (broadcom drivers), but when I try to enter *ndiswrapper* commands it tells me that the ndiswrapper command isn't found.

I thought it was installed with base install of 6.06.1?

Also, all the instructions I can find for setting up wireless cards with broadcom chipsets start with "we assume you have a wired connection to the internet..."

I don't.  I dual-boot to my windowsxp install to get online, since my PCI card is auto-detected by windows...

Is Ndiswrapper installed, but just not in the "path?"  If not, can I download it from windows and install it from my fat32 drive?

Any help is appreciated!


You have to install ndiswrapper-utils

Open a terminal and:

```
sudo apt-get install ndiswrapper-utils
```

After that it should work, dunno why they keep that back anyways. Maybe a bug?


Kind regards,


TFX

---

### Post by ComplexNumber on 2006-08-19
> **random.brown said:**
> Hello,

I'm trying to set up my wireless PCI card (broadcom drivers), but when I try to enter *ndiswrapper* commands it tells me that the ndiswrapper command isn't found.

I thought it was installed with base install of 6.06.1?

Also, all the instructions I can find for setting up wireless cards with broadcom chipsets start with "we assume you have a wired connection to the internet..."

I don't.  I dual-boot to my windowsxp install to get online, since my PCI card is auto-detected by windows...

Is Ndiswrapper installed, but just not in the "path?"  If not, can I download it from windows and install it from my fat32 drive?

Any help is appreciated!
no, its not installed by default. what ndiswrapper packages have you installed? i have 3 on my system - ndiswrapper, kmod-ndiswrapper, ndiswrapper-kmdl. perhaps you're missing one of them.

---

### Post by mikecar52 on 2006-08-19
> **random.brown said:**
> Hello,

I'm trying to set up my wireless PCI card (broadcom drivers), but when I try to enter *ndiswrapper* commands it tells me that the ndiswrapper command isn't found.

I thought it was installed with base install of 6.06.1?

Also, all the instructions I can find for setting up wireless cards with broadcom chipsets start with "we assume you have a wired connection to the internet..."

I don't.  I dual-boot to my windowsxp install to get online, since my PCI card is auto-detected by windows...

Is Ndiswrapper installed, but just not in the "path?"  If not, can I download it from windows and install it from my fat32 drive?

Any help is appreciated!

maybe, maybe not.
try sudo ndiswrapper -l
if anything comes up yes it is there
I have had to download the package for mine.
similarly for slmodem

---

### Post by harisund on 2006-08-19
Come on people, the original poster is complaining that he doesn't have any sort of internet, and advices such as "apt-get install" is being given? How do you expect the poster to be able to do that? 

Anyway, head over here with your Windows partition [http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils) and download the .deb file and save it somewhere. 

Once back into Linux, navigate to your Windows partition where you saved the .deb file (if recognized by default you will find it in /media/hda1 or whatever) and use "sudo dpkg --install name_of_deb_file.deb" and ndiswrapper-utils will be installed. 

Then make sure you know where your wireless card Windows drivers are. Once again, probably somewhere in your Windows partition. Navigate again there and follow your ndiswrapper instructions. 

I hope you know what you are doing with that ndiswrapper? Otherwise post back here and you are likely to receive help again.

---

### Post by random.brown on 2006-08-19
Thanks for the post, I was able to get ndiswrapper installed; now to get the wireless to actually appear!

I'll keep at it, thanks again.

---

