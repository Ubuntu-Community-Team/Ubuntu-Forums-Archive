---
title: "HELP! Can only start in recovery mode!"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by sublime ph03nix on 2007-06-10
So here's the deal.

I got ubuntu 7.04 today, installed everything on my hard drive and I get to the GRUB loading screen.  I go to normal ubuntu mode, and the system loads a few things in text on the screen then the screen goes black and the monitor goes to sleep.  It seems like the drivers for the graphics card are maybe a problem, but I CAN get into recovery mode and get into the GUI and to the desktop.  

Does anyone know a solution for this?

Also, any time i try to move files from a usb flash drive to a folder ubuntu tells me i do not have the priveliges to do it.  Any suggestions?

---

### Post by Haegin on 2007-06-10
Can you post more information on the graphics card you have and any relevant information from logs that you can find. In particular check the xorg log

---

### Post by gerscht on 2007-06-10
As above, plus can you log in to an other console via CTRL-ALT-F3?

---

### Post by kguse2b on 2007-06-10
Same here! I'm a beginner in Linux (of any kind) and I'm looking at the same black screen. First I reset the unit and I went with the recovery option. I got the screen with the text :( . Dead end for me there, as I don't know any commands for the linux console. So, I typed EXIT and then pressed ENTER. And the damned thing worked: I got the GUI asking me for the user name and pass. After that all OK... for a while...: "Ubuntu has updates for you". OK lets make the update. after that I activated the restricted driver (nvidia) and restarted. No longer work in any mode. I applied the same procedure as before but I got a scrambled error message about the X something (I can't remember what, I guess is the GUI) not being able to load. Sorry for my poor English.

My system:
CPU: Intel Core 2 Duo E6600 (2400MHz)
MB: Asus Striker Extreme (680i)
RAM: 2GB (Corsair) 2x1GB
Video: 8800GTS 640MB (Nvidia)
HDD: WD 500GB (Partitioned like this: 30GB NTFS PRIMARY with WinXP system install; 398GB NTFS  LOGIC with DATA; ~1.2GB LOGIC linux SWAP ~26GB linux Ubuntu). The NTFS and the linux swap are on the same extended partition).

I will appreciate any help. Thank you.

---

### Post by kguse2b on 2007-06-10
I also could not start the CD GUI at first, but I pressed F4 and changed the resolution to 1280x1024x32bit (the native resolution of my LCD is 1280x1024) and then it worked. Now I'm writing from this version of Ubuntu.

---

### Post by sublime ph03nix on 2007-06-11
> **Human Prototype said:**
> Can you post more information on the graphics card you have and any relevant information from logs that you can find. In particular check the xorg log

I'll just post the full system specs just in case.

AMD Athlon 64 3700+ @ 2400
ATI Radeon x850XT PCIX x16
2 GB DDR266 ( :( )
Abit kN8 Ultra -- nVidia nForce 4 ultra
WDC 160 GB SATAII
Hitachi 20 GB IDE
SB Audigy 2
Linksys Wireless PCI adapter -- WMP54GS

I really have no clue how to continue, especially since I use Linksys wireless internet and from what I heard Broadcom chipsets are not supported in Ubuntu, at least not for my model. So I cant even be in linux while I read stuff :(

Any help would be greatly appreciated, thanks.

---

### Post by Haegin on 2007-06-11
You will both need to use the console to fix this (which is fine because the console is powerful and fun, honest!). When you are in the console you will need to check your xorg.conf file to see what graphics driver it has tried to load.

kguse2b - I think your problem is definitely linked to your graphics card and I suspect that a card that new may not be supported by the drivers that are included by default with Ubuntu. This isn't a problem as we can sort this but lets get back into a graphical environment first.

At the command line type the following (pressing return after each one):
```
cd /etc/X11/
```
This changes to the /etc/X11/ directory
```
sudo cp xorg.conf xorg.conf.bak
```
This creates a backup of the xorg.conf file just in case. You will need to enter your password to do this.
```
sudo nano xorg.conf
```
This opens the xorg.conf file in nano, a text editor.
Scroll down the file until you find the line:
Driver       "nvidia"
Change the "nvidia" to "nv" and save the file by pressing Ctrl+O then close nano by pressing Ctrl+X (I know the key combinations seem weird, don't ask why - I don't know myself)
Now this file has been altered we can tell X, the graphics manager to try and start again.
```
sudo /etc/init.d/gdm start
```
Hopefully this should get you to the normal login screen and you will be back to normal again. Let me know what happens and if it works I will try and help you get your Nvidia 8800 working with the official drivers.

sublime ph03nix - I am not so sure about the cause of your problem so I need a bit more information. Did the graphics ever work? If so what caused them to stop working, for example did you install the official drivers or try and install beryl or use the desktop effects stuff?

Don't try the stuff for kguse2b as your graphics card isn't an nvidia card so it definatly won't work and will make everything worse.

---

### Post by sublime ph03nix on 2007-06-11
Well, the graphics have never worked in normal mode, it just cuts to the black screen after a screen of really fast illegible text.  Then i go into recovery mode, type exit then enter, and i get to the gui and the graphics work there.  i've tried installing ATI's official drivers and i installed them off of a flash drive but to no avail; still the same problem.  It is entirely possible, however, that im retarded and did it wrong though :p

---

### Post by sublime ph03nix on 2007-06-11
I found a new message screen today that may shed some light on the problem.
Before the gui in recovery mode I'm at a console screen with a little blinking cursor thing after "root@cam-ubuntu:~#"

If I type something, occaisionally (every few minutes or so) a little message pops up in the console:

> firmware_helper[4639]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:05:06.0' with driver '(unknown)'

[   86.526460] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

So yeah, thats the message.

Hope that helps to solve the problem.  Seems like somethings missing maybe?

---

### Post by Haegin on 2007-06-11
That looks like its trying to load firmware and normally I think that is for wireless - do you have wireless on this PC and is it working?

---

### Post by Nythain on 2007-06-11
that would the the broadcom wireless adapter... that company sucks... havent had to deal with them, just know they are a pain to get to work in linux

---

### Post by sublime ph03nix on 2007-06-11
I do have wireless.

I use Linksys Wireless PCI adapter with speed booster -WMP54GS.  From what I've read, this adapter is not supported in linux by broadcom or by linksys and I cant find any 3rd party drivers.

As an added bonus I now cannot get to the gui in recovery mode >.>

Should try a clean install of 6.10 or 6.06 ubuntu an just get rid of fiesty fawn?

---

### Post by kguse2b on 2007-06-13
Thank you, Human Prototype. I will follow your advice as soon as a get to my computer.

---

### Post by kguse2b on 2007-06-13
After I started in recovery mode, I did exactly as you said and all worked out just fine. I started the GUI and after that a message popped up saying "Internal error / failed to initialize HAL!". Hmm, that I manage to find out is "Hardware Abstraction Layer". I guess it got confused about the graphical card, or something.
Well, after restart I find myself in the same problem. If I start normally I get a black screen and nothing more. I have to reset from the front button and go with the recovery. After that: sudo /etc/init.d/gdm start, and back to the error message in GUI.

---

### Post by fergatron on 2007-06-14
Hey...

So one question...Are you running the x86 (64bit) Version of Ubuntu...

I had the same problem when I tried...the whole blank screen monitor shut off thing, 

There's a bug that hasn't been solved in the 64bit release of Feisty I've read about this in many places. Try doing what I did and installing the 32bit Version...That worked like a charm for me on generic boot, so download, reformat, install and tell me if that soved your problem ( it did for me) I did want to run the 64bit version but hey it hasn't been too bad...

---

### Post by kguse2b on 2007-06-14
Yes, I'm running the 64bit version, as I have Intel Core 2 Duo, and I wanted the extra performance. Also, in WinXP 32bit I can't see more than ~3GB of RAM, having 4GB installed. Even if now I only have 2GB (for that reason), I plan to increase that to 4GB in the near future.
I'm not sure if Linux has the same limitation as Windows. So, what you are saying is that with the 32bit version Ubuntu 7.04 my video card will work fine? I guess I'll try that. Nothing to lose yet.
I'm not sure how to remove the Linux, as it installs it's boot loader.
If I just format the partition with Linux and install another version (32bit) it will know to remove the old version from the boot list?

After one day: :(

No good. Same with the 32bit version. Only some variations to the path towards the black screen. It will start the Live CD, but after install I get the same problems.  ](*,)

---

