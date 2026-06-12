---
title: "On-board Graphics Install Issue"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2007-10-07
So, I have a computer that is having problems caused by it's on-board graphics chip. It has a GeForce 2 MX 200 installed and I disabled the on-board in the bios, but ubuntu tries to use it anyway. I with the card in my computer automatically uses it, but when ubuntu boots up, it tries to switch. Through the restore kernel, I've edited xorg.conf and done dpkg-reconfigure xserver-xorg, but it wont go in to kdm. It says starting kdm, but then the screen blinks and it continues with a list, even though it says [ OK ] next to kdm. I had it woking once with the closed source nvidia drivers, but I forgot how I did that. If you could tell me how to install the nvidia driver (enable the restricted driver) from terminal completely or another way to fix this problem, it would be greatly appreciated.

---

### Post by julian67 on 2007-10-07
Linux doesn't really use the BIOS, it does all the hardware detection itself so that's why disabling the card in the BIOS has no effect. What you can do is blacklist the driver for the adapter you want disabled. If you look in /etc/modprobe.d/ you'll see a file called blacklist. Find out the name of the driver for your on-board graphics adapter and add it to that list and reboot and your PC should boot using the nvidia card.

---

### Post by LowSky on 2007-10-07
I disabled my onboard graphics in the BIOS and they dont get loaded. I have also diabled hard drives and pci slots and linux doesn't load those either.

I dont have an aswer but, Julian67 I dont think your right.

---

### Post by julian67 on 2007-10-07
> **LowSky said:**
> I disabled my onboard graphics in the BIOS and they dont get loaded. I have also diabled hard drives and pci slots and linux doesn't load those either.

I dont have an aswer but, Julian67 I dont think your right.

Have a look at LinuxBIOS, it's very interesting. 

GNU/Linux does its own hardware detection independently of the BIOS settings. That's why  people with onboard sound or graphics can have a lot of trouble disabling them in favour of PCI/AGP upgrades when they do it in BIOS. If it's disabled in BIOS how is the OS still using the hardware???? Answer: the OS ignores the BIOS and detects the hardware itself. 

Traditional BIOS is hardly needed for Linux, all that is needed from the BIOS is to load a bootloader. There's a good article: [LinuxBIOS - A truly GPLed Free Software BIOS](http://linuxhelp.blogspot.com/2006/11/linuxbios-truly-gpled-free-software.html)

---

### Post by Dapilot1 on 2007-10-10
Blacklisting did not work. Does anyone know how to install the restricted drivers from a terminal?

---

### Post by julian67 on 2007-10-11
> **Dapilot1 said:**
> Blacklisting did not work. Does anyone know how to install the restricted drivers from a terminal?

try

```
sudo apt-get install nvidia-glx-legacy
```

afaik you need the legacy driver for GeForce2

---

### Post by Dapilot1 on 2007-10-22
So I waited and retried with 7.10. Still no success. This time I used the Live CD that I used on my main computer and I got absolutely nowhere. Is there a way to do a text install with the Live CD? Is that what the OEM install is? I don't want to use more CDs than I need to.

---

### Post by Dapilot1 on 2007-10-22
Oh, also I have yet to try the code you gave me. I'm waiting to use it when I get 7.10 almost working. Thanks for the help though.

---

### Post by julian67 on 2007-10-23
You need the alternate CD to do a text based install. This is not the same thing as an OEM install. 

If you have an internet connection then ```
sudo apt-get install nvidia-glx-legacy
``` will likely solve this problem. It isn't code or a magic incantation, simply a command. 

sudo = do this as administrator

apt-get = the package manager. This is your tool for installing/uninstalling/managing all the software on your PC

install = install

nvidia-glx-legacy = is, I believe, the correct driver for your card

If you do this then the driver will be installed and your system's graphics card config will be automatically updated to use it. You would need to reboot or <alt><ctrl><backspace> to restart X. 

Assuming this works on your Feisty install you could then go ahead with the upgrade to 7.10 and it will automatically upgrade, keeping the correct driver.

An alternative would be to physically remove the nvidia card, boot up into  the normal graphical environment,  then use Synaptic to install nvidia-glx-legacy, then physically re-install the graphics card and then run ```
sudo dpkg-reconfigure xserver-xorg 
```

The first method is better.

---

