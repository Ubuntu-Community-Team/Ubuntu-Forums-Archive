---
title: "[SOLVED] installing memory map"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jboy012000 on 2007-10-31
Hi All,

I use a programe called memory map which is all the o/s maps of the uk which I can transfer GPS data to my GPS unit, I have read on other posts about using something called wine? were do I find wine and how do I use it to install memory map.

Thanks in advance.

---

### Post by Jaco Du Toit on 2007-10-31
To install a default configuration of wine (that may or may not work with the Memory Map program) simply type:

```
apt-get install wine
```

in a terminal or install it via synaptic. Then from a terminal run

```
winecfg
```

Set your default windows version and leave the rest on default. That basically takes care of the default wine install. Now to install the program you might be able to run the following command from a terminal: 

```
wine MemoryMapInstall.exe
```

Where you of course substitute MemoryMapInstall.exe for the actual name of the install program. If the install is a .msi file, for instance MemoryMapInstall.msi then run

```
msiexec /i MemoryMapInstall.msi
```

If you are lucky, then it works. Wine is unfortunately a bit of a hit or miss affair. Anyways, asuming you get through the install process, the program will be located in:

/home/username/.wine/drive_c/Program Files/ ...

Browse to that directory (where username is of course your own username) in the terminal and issue the command

```
wine memorymap.exe
```

(Or whatever the program is called)

Good luck. I managed to get quite a number of my windows programs to work very well in wine, even including some games like World of Warcraft.

---

### Post by jboy012000 on 2007-11-02
Thanks for the info mate I will give it a blast.

---

