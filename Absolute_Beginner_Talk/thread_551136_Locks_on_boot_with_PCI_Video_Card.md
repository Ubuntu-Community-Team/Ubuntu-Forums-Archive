---
title: "Locks on boot with PCI Video Card"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by OziD on 2007-09-14
I just recieved an EVGA eGeforce 6200 PCI card (256MB of ram, 128bit) for a Dimension 2350 I inherited. 

It has Intel Onboard graphics that work fine for normal usage. But I want to take advantage of the Desktop Effects, and Compiz when Gutsy comes out.

So I bought the card. The problem is, no matter what way I install it, it always locks on the "progress bar" screen. I've installed the card physically and ran ENVY, I've manually installed drivers, I've just changed xorg.conf for the generic drivers. No matter what I do, it locks at the progress bar (about three "blocks" in).

I can boot the computer up when the bios is set to ONBOARD video instead of auto detect. But after I change try and install the board in ubuntu, it fails.

Let me know what you need from my side for you to help me figure out my problem. When I boot in recovery mode, it goes along fine for a few seconds until it hits a "==========================" and it always seems to be pretty random where it is. It's never at the same point in the boot, that I can tell.

---

### Post by alienexplorers on 2007-09-14
Is there a way on your system to disable on board video.  It sounds like a conflict between the two.

---

### Post by OziD on 2007-09-14
Yeah in the BIOS, after I install the nvidia driver, I disable the onboard. (Its actually autodetect, but it doesn't show anything on the onboard monitor when I have it on auto).

Even if I install it with just the new card installed and in use, it locks on boot.

---

### Post by OziD on 2007-09-15
this is the fastest moving board ever.

Any suggestions?

---

### Post by OziD on 2007-09-15
here's the screen when i try and boot in recovery mode. it just hangs there, i can't get to anything. I can use the system fine if i Install with the onboard video (and using the onboard video as the display)

But after I change the driver to NV, or any of the other nvidia variants, this happens every time.

---

### Post by alienexplorers on 2007-09-15
When you burnt your disk did you do it at 4x or slower.  Did you check the md5 checksum.

---

### Post by OziD on 2007-09-15
it shouldn't be a disk problem... this has happened with two edgy disks, and a Feisty disk. but no i didn't burn at 4x or slower.


I don't know what an md5 checksum is :|

---

### Post by OziD on 2007-09-15
I have the system up and running with the onboard video, not the video board. 

If you have any suggestions, nows the time to chime in ;)

---

### Post by w4ett on 2007-09-15
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

### Post by OziD on 2007-09-15
I got it to work. In the Bios, however, I have to have it set as "Onboard". If it's in Auto (would select the PCI card), it won't boot. I used the restricted drivers manager as you suggested. 

I am not completely convinced that it is working, though. Desktop animations are still slugish. I'm going to wait until I get more RAM before I complain, though. :P

I am only running 384MB right now! :(

Thanks guys.

---

### Post by alienexplorers on 2007-09-15
I am running Ubuntu on a K6-III 450mhz system with 384mb memory, and a FX5200 video card.  System runs most things fine.   alittle choppy in games, but what am I to expect.

---

### Post by Panda X on 2007-09-25
Sorry to bump but I have the same exact situation. Same hang on three bars. Same hang on ================ in Rec Mode. Same 6200 PCI. Same Intel Onboard. The thing is, I can't get it to work. When I try to use the Restricted Drivers, same thing happens. When I use Restricted Drivers + Onboard like the OP did X fails to start. Then only way to boot is use this crappy Intel. Can anyone help?:(

Once again sorry for that bump but after 3 hours I got it.

---

### Post by michaelaly on 2007-10-01
I have had the same issue for a while using an eVGA MX 4000 PCI video card on a Dell Dimension 2350, 1gb ram.
I am unable to run LiveCDs or install Linux(locks on boot). I have tried Ubuntu(Feisty and Dapper), Freespire, and Knoppix with the same result. 
The only way I get any linux to run is to physically yank the video card out of the computer. Changing the BIOS setting has made no difference. Using VESA as a bootup option didn't help. I'd love to know if anyone can fix this since I'm stumped and stuck with XP on that machine. 
thanks

---

### Post by michaelaly on 2007-10-05
Got it working. 
The only problem is that now I can't see the bootup screens, so if I need to go into the BIOS for any reason I have to switch the monitor cable over to the onboard video...but it works.
thanks to everyone.

---

