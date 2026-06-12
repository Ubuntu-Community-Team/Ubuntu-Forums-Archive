---
title: "[SOLVED] Help! Can't enable Nvidia Driver!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by TheThinker on 2007-05-13
Hello everyone. I'm a newbie to Linux, and I just installed the Feisty Fawn version of Ubuntu three days ago on my desktop PC. The problem is that under Restricted Drivers Manager it cannot let me enable the driver for my Nvidia GeForce4 MX 4000. It starts off with the driver "not used". I press the box next to the driver, press okay on the next screen confirming my choice, and then nothing, nata...zip. The driver still says it's not being used, and the process repeats itself. I have the same problem through the desktop-effects option. Feisty tells me to enable the Nvidia driver so that I can proceeed. I press okay on the "enable" option and it then tells me to restart when the driver is working. I restart, and still nothing! The Restricted Drivers Manager still says it's not being used (check-box is empty). 

Mind you, I don't have internet connection for this particular computer, yet, so any driver-installation through the web is currently unavailable to me. I could go ahead and hook it up to a phone-line, but I don't know if I need to install/configure an internet-provider service like SBC Yahoo (which I use in these forums). That's something I want to avoid so that I can go to installing Beryl and WineX, but if I have to I will.

To be specific, I installed Ubuntu WITH the Nvidia card already placed inside the PC's PCI slot (don't know if that matters). My bios settings were set to AGP for the primary display source in the beginning, and is (and alway has been) plugged into the system's integrated Intel graphics chip. I know that is working fine. The Nvidia card, however, never worked out. I wonder if it's just a hardware issue; it worked fine on Windows XP before though.

I looked at my Hardware Information and both of my graphics devices (the Nvidia PCI card and the Intel Integrated Graphics Chip) are listed as "PCI" buses. Shouldn't my Integrated Graphics Chip be listed as AGP, as listed in my BIOS configurations? I'm thinking I need to reinstall the whole O.S. without my Nvidia card plugged in, but I could be wrong. I've already did a clean re-install of the O.S., except I forgot to take out my Nvidia card before doing so in case my theory is correct. Oh well. Perhaps it's because I installed Ubuntu in safe-graphics mode?

I decided to turn on the computer WITHOUT the Nvidia card plugged into its PCI slot to see if it will fix itself. As predicted, the Restricted Drives Manager doesn't detect any hardware needing those changes. I then go to desktop effects, enable it, and then get a completely white screen with just my curser. I'm betting that's a seperate problem altogether, but probably related. The Intel Integrated Graphics chip still read as a PCI bus though. Now the Nvidia card is plugged in again, since I don't want to leave it out gathering dust.

Last yet not least, with or without my Nvidia Geforce4 MX 4000 plugged in, every time I "log out" I get just a black screen. My monitor doesn't say that there's no signal, so I'm completely lost on why this occurs. Sound still works, so I can just type in my password and hear the O.S. start. Restarting the computer makes everything visible again. Very odd.

I just wanted to give everyone as much info as needed. Please remember that my Ubuntu computer has no internet connection, so any off-line solutions are greatly appreciated. Otherwise I'm pooped.

---

### Post by Bachstelze on 2007-05-13
For legal reasons, the nvidia drivers are not included in Ubuntu so you'll have to download them anyway.

---

### Post by KSI on 2007-05-13
May or may not help. I noticed nVidia drivers in the included packages of [Automatix2](http://www.getautomatix.com/wiki/index.php?title=Installation). Might help.

---

### Post by TheThinker on 2007-05-13
Is Automatrix2 an off-line application? If not, then I don't think I'd like to go through the trouble of getting internet connection. But if I must I will.

---

### Post by Bachstelze on 2007-05-13
You must. You'll need an Internet connection to get both the nvidia drivers and Beryl. And I strongly recommend you don't use Automatix.

---

### Post by Nythain on 2007-05-13
you say you dont have a net connection... then its not installing them because it cant... they arent bundled with the distro for legal reasons as hymm said... so in order to install them, ubuntu needs to get them from the repositories, wich just isnt gonna happen without a connection to the net.

automatix2, even if they could get it installed without a net connection to download that either, wouldnt work also, for the same reason.

you can try getting on a computer with a net connection and heading over to
[http://packages.ubuntu.com/feisty/x11/nvidia-glx](http://packages.ubuntu.com/feisty/x11/nvidia-glx)
downloading the package, and any depencies it has that your dont meet and install it all manaully with dpkg

but that could lead to more dep issues wich lead to more dep issues... i would suggest just finding a way to get on the net, even if its temporary, and doin it up

---

### Post by KSI on 2007-05-13
> **HymnToLife said:**
> You must. You'll need an Internet connection to get both the nvidia drivers and Beryl. And I strongly recommend you don't use Automatix.

Not to get off subject, but I've never had problems with AutoX. Why would you not recommend it?

---

### Post by Bachstelze on 2007-05-13
There actually won't be much dependency issues as the restricted-module package is on the Ubuntu CD and all other things nvidia-glx depends on are installed OOTB.

@KSI, just hang around here for a while, you'll see that Automatix-related problems are not uncommon.

---

### Post by KSI on 2007-05-13
[Hymn] Eh, I'll do. I ran it with Debian for some time, without any problems. That being said, I've only used it for small, stable applications.

---

### Post by TheThinker on 2007-05-13
From what I read it looks like I'll need to (gulp) go on the net to do this. I just tried Automatrix2, and it said "Dependency is not Satisfiable: Python2.4", so I guess the internet is the place to go.

Question: Is it as simple as plugging the PC into a phone-line with my modem, or do I need an internet-provider such as SBC Yahoo (which I currently use to go through the forums on a different PC)? If any of you have guide-files or links to guides, that would be great. 

By the way, thanks for the feedback. I never expected this amount of help in such a short period of time. I'll be back tomorrow to see what you think.

---

### Post by Bachstelze on 2007-05-13
Forget Automatix.

If you have a dialup modem, it might be much more trouble to setup than the nvidia drivers. Just grab the nvidia-glx package in Windows, copy it to your Ubuntu and install it.

[http://packages.ubuntu.com](http://packages.ubuntu.com) <= get the package from here

Basically, whet you need to do :

In Ubuntu, install the restricted-modules matching your current running kernel :

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

Then in Windows, download the nvidia-glx package and copy it to your desktop in Ubuntu. Then do

```
sudo dpkg -i ~/Desktop/nvidia*.deb
```

If all went well, you can configure your X to use the driver :

```
sudo nvidia-xconfig
```

restart X :

```
sudo /etc/init.d/gdm restart
```

and the nvidia logo should appear.

---

### Post by TheThinker on 2007-05-13
Thanks Hymn. What do you mean by "Then, in Windows"? Do you mean that I have to switch over to the Windows XP in the same PC we're talking about? If that's the case, then I have to say that I completely erased my Windows XP in Ubuntu's installation; I didn't think I'd be needing it.

Yes, a day hasn't gone by yet, but I decided to check back since my plans have changed.

---

### Post by TheThinker on 2007-05-13
Oops. Stupid question that. You must mean I download the package through my OTHER computer, which uses Windows. Of course. My fault.

---

### Post by TheThinker on 2007-05-13
Should I use the AMD64, or the i386? My computer uses a 2.8ghz Celeron D processor, if this helps in answering my question.

---

### Post by Bachstelze on 2007-05-13
The i386, most likely. Just to be sure, you can type

```
uname -m
```

in a terminal and see what that tells you. If it's i386 or i686, go with the i386 version. If it's x86_64 or something like that, go with the amd64.

---

### Post by TheThinker on 2007-05-14
I'm finally back! Thankyou very much Hymn. I'll do what you say. I'll let you know in a while if it worked or not.

---

### Post by TheThinker on 2007-05-14
Okay, I did your first step just now (installing restricted modules). Here's how the terminal reads thus far:

[I]megadeuce22@Big-O:~$ sudo apt-get install linux-restricted-modules-$(uname -r)

Password:

Reading package lists... Done

Building dependency tree       

Reading state information... Done

linux-restricted-modules-2.6.20-15-generic is already the newest version.

linux-restricted-modules-2.6.20-15-generic set to manual installed.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

megadeuce22@Big-O:~$[/I]

From what I read, this appears to be good.

---

### Post by TheThinker on 2007-05-14
Well, everything seemed to work fine up to the point that you said that the Nvidia Logo should appear. After the last step, the screen changed so that the only things I see were the desktop's wallpapaper and thecursor (which does not move). There are no toolbars or buttons at this point, just that.

Is this because my BIOS video settings were set to AGP instead of PCI where my Nvidia card is placed? I'm thinking of restarting to set it to PCI, but I don't want to accidentally screw up where I left off.

At least the Terminal said it backed up the xconfig file.

---

### Post by TheThinker on 2007-05-14
I did it. I was just too impatient. You were right Hymn, and I was right too. I restarted my computer, switched my BIOS video output to PCI, and BOOM! It's done. The Nvidia logo flashed before I saw my login screen. Everything works now! The Restricted Driver Manager says it's working, Desktop Effects works as far as I see, and whenever I log off the screen does not stay black! 

Thank you very much to everyone else who helped. This must be such a common problem; I was surprised that the system did not come with a complete manual upon install to guide me through this process. Oh well. Ubuntu is free, and so far I'm thinking it's worth the hassle in these past 4 days.

Don't be surprised if I post another question on the forums. I plan to install WineX and Beryl soon (salivates). God bless you.

---

