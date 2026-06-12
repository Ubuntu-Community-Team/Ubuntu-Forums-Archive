---
title: "[SOLVED] IBM NetVista Xorg problems"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by duhsutter on 2007-09-20
So I actually installed Ubuntu Feisty Fawn on a hard drive on my first computer. I put the Hard drive into my NetVista and the start up stalls once

GRUB Loading Stage 1.5
GRUB Loading, please wait Press 'Esc' to enter the menu...2

I'm pretty sure that usually counts down, but not on this machine. Anyway, I hit escape and attempt to start in recovery mode. The Xorg error comes on... Tells me 

no screens found

and some other stuff. Anyway, I've tried the reconfig steps listed and I can't figure it out. I think it's the driver... but I'm not sure how to beat it.

Pentium 4
512Mb RAM
30GB Hard Drive
NVIDIA VANTA (I Think, I'm getting this computer used... so I'm not sure about that.)

Anyway, I'm running Ubuntu, KDE and xubuntu on my hp, but it only has a Pentium III, 256 RAM and no room for upgrades. So, I'm eager to get this NetVista up and running, especially before Gutsy Gibbon. Thanks.

---

### Post by jimrz on 2007-09-20
if I get it correctly, you have installed ubuntu on your hdd on one machine and are now trying to run from that hdd after moving to another machine with significantly different hardware/specs. if that is the case, I would definitely suggest backing up any data from that hhd that you need to retain then running a fresh install on your new machine. believe this would prove to be much easier, simpler, effective and less time consuming than trying to fix all the issues that your current situation poses on a hunt and seek one by one basis. 

that said, if you created a separate /home directory on the previous install you can likely retain that, thus saving much of your stuff, and only re-intsall your / directory. if this is your case, be sure to tell the partitioner to mount /home as /home but NOT to format it.

---

### Post by w4ett on 2007-09-20
> no screens found

and some other stuff. Anyway, I've tried the reconfig steps listed and I can't figure it out. I think it's the driver... but I'm not sure how to beat it.

I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by duhsutter on 2007-09-21
I haven't tried it yet, but I'll see how that goes, I've tried 

"sudo dpkg-reconfigure -phigh xserver-xorg"

but never the startx command. So I'll give it a shot tonight... thanks a lot.

---

### Post by duhsutter on 2007-09-21
> **w4ett said:**
> This should  get you to a GUI desktop.



```
 (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 6 .....
(==) Using config file: "/etc/X11/xorg.conf"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

```

I'm gonna try and reinstall Ubuntu... we'll see what happens, but I think I've tried, can anyone fix this?

---

### Post by duhsutter on 2007-09-22
> **jimrz said:**
> if I get it correctly, you have installed ubuntu on your hdd on one machine and are now trying to run from that hdd after moving to another machine with significantly different hardware/specs. if that is the case, I would definitely suggest backing up any data from that hhd that you need to retain then running a fresh install on your new machine. believe this would prove to be much easier, simpler, effective and less time consuming than trying to fix all the issues that your current situation poses on a hunt and seek one by one basis. 

that said, if you created a separate /home directory on the previous install you can likely retain that, thus saving much of your stuff, and only re-intsall your / directory. if this is your case, be sure to tell the partitioner to mount /home as /home but NOT to format it.

I tried running Ubuntu Live, It gives me same errors as if I were running Ubuntu off the Hard drive. I think I might try using the other machine to enable drivers, and see if that will work.

---

### Post by duhsutter on 2007-09-22
GOT IT!!! I had to change the video set up in the BIOS to allow 8MB for video. The computer is working awesome now. Thanks for everyone's help. Also... it still stalls while loading grub

```
 GRUB LOADING Please wait... 2
```

But I'm not terribly worried about that.

---

