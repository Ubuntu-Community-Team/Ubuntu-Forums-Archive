---
title: "Nvidia 8800gt in Ubuntu Studio"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by armond21 on 2008-04-14
I installed Ubuntu Studio, tried to run it, and it gave me an error: 
Failed to launch xserver: no screens found.
The release of Ubuntu Studio I am using is the latest from October, 07.
any thoughts?

My system specs are:
Gigabyte M57SLI-S4 Socket Am2 mobo
AMD Athlon X2 5000+ Black Edition 
Scythe Katana 2 Cooler
2gb PQi Turbo ram ddr2 800 cl4
PNY 8800GT 512mb

---

### Post by njparton on 2008-04-14
Try using envy (google it) to install the latest nvidia restricted drivers.

---

### Post by armond21 on 2008-04-14
Is there a text command I have to use to install envy as I do not get as far as the linux desktop?

---

### Post by njparton on 2008-04-14
Yes, envy can work from the command line.
 
If you google it, there's advice on the envy site for how to use it that way.
 
Google: ubuntu envy

---

### Post by armond21 on 2008-04-14
i"ve been looking for the text command to install envy and i'm not finding it. sorry if i'm being a pain, i just really want to figure this out.

---

### Post by PmDematagoda on 2008-04-14
> **armond21 said:**
> i"ve been looking for the text command to install envy and i'm not finding it. sorry if i'm being a pain, i just really want to figure this out.

If you want you could install the driver manually:-

1) Install the prerequisites for the driver with:-
```
sudo apt-get install build-essential
```

2) Download the Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

3) Install the driver:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

4) Start the X-Server:-
```
startx
```

See if that allows you to start the X-Server properly.

---

### Post by pedro_orange on 2008-04-14
Good morning!

I have an nvidia 8800GT & had similar issues - but I use 7.10 (Not studio - so I may be slightly off the mark here)

I take it you booted up to a LiveCD? You must have got some GUI there? 
How did you get to the point where X is failing? Did you install video drivers? Or just install the OS?

I had a problem with XServer not running at the correct resolution for my monitor so it could possibly be that. (Although I only noticed this problem after I installed my drivers through restricted manager) 

I did a:

```
sudo dpkg-reconfigure xserver-xorg
```

Chose the appropriate resolutions and wh00p working.

---

### Post by armond21 on 2008-04-14
I just attempted to install the drivers through nvidia as suggested above but they are not compatible with the kernel in Studio. I believe i read on another forum that there is a low latency kernel in Ubuntu Studio. I do not know what that means any deeper than i know the definition of all the words used above.
I actually had the standard ubuntu linux gutsy 7.10  running fine but i wanted to try Studio for the multimedia creation and editing aspects.
> **pedro_orange said:**
> 


I take it you booted up to a LiveCD? You must have got some GUI there? 
How did you get to the point where X is failing? Did you install video drivers? Or just install the OS?



I installed from the iso and tried to launch, it gives me the error as its initializing. ive acutally never seen a desktop.

---

### Post by njparton on 2008-04-14
The best bet may be to install the programs and codecs studio uses in your standard ubuntu version? There must be a list of these somewhere.

---

### Post by trashie on 2008-04-14
Hi there,

Just a small comment to tell you that you can use envy in command line by taping : 
```

$ sudo envy -t

```

Remove first old Nvidia drivers (since you tried to install it manually) using envy, and then reboot.
After reboot, run again envy, and install nvidia drivers.

Good luck,

Mathieu

---

### Post by armond21 on 2008-04-14
thanks for all the suggestions. I have another studio machine with a card on the supported driver list for that build, so ill try that tomorrow.

---

