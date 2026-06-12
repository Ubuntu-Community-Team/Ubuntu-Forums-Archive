---
title: "What is the best driver for a GeForce 6100 in Ubuntu?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-08
Will this driver work?
[http://www.nvidia.com/object/linux_d..._1.0-8174.html](http://www.nvidia.com/object/linux_d..._1.0-8174.html)

This is the mobo I am using:
[http://www.abit-usa.com/products/mb/...es=1&model=332](http://www.abit-usa.com/products/mb/...es=1&model=332)

I just installed a fresh install of Ubuntu 6.10 and none of the drivers seem to work... graphics, sound...  I just need someone to tell me which drive would be best for the integrated graphics card on this motherboard.

---

### Post by Paul41 on 2007-04-08
Your link for the driver took me to a "page not found".

nvidia-glx which is available in the repository should be what you want.

---

### Post by kc5hwb on 2007-04-08
[http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html)

I think that is the one that I installed thru Synaptic and it didn't work.

---

### Post by mikewhatever on 2007-04-08
According to [this page]("http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html"), the driver is correct. You might need to change the driver in your xorg.conf. Assuming you have no GUI,
> sudo nano /etc/X11/xorg.conf
look for the following section and make sure the driver selected is nvidia. Then Ctrl+O to save and Ctrl+X to close.
> Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection


---

### Post by kc5hwb on 2007-04-08
Well, I changed the Driver "nvidia" part and X wouldn't load, so I had to go back to the VESA driver, which it originally detected, just to get X to load.

And yes, that page is the one that I tried to link from and the one that I downloaded the driver from.  But I can't get this to work:
```
sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
```

If I boot from GRUB into the cmd line without X and try to run that, it tells me it isn't recommended to run at Level 1.  I try to type "telinit 3" and it boots X.

---

### Post by Paul41 on 2007-04-08
Do you have the Linux restricted modules installed for your kernel?  You will also need that for it to work.

---

### Post by kc5hwb on 2007-04-08
Would that be in the xorg.conf file?  Where would I look to find that?

But again, I haven't been able to successfully install that file.

---

### Post by Paul41 on 2007-04-08
> Would that be in the xorg.conf file? Where would I look to find that?

```
sudo aptitude install linux-restricted-modules-generic
```

This assumes you are using the generic kernel.  If not replace the generic part with which ever kernel you are using.  If you install this it might fix the problem with the drivers you were trying to use from Synaptic.

---

### Post by Paul41 on 2007-04-08
> And yes, that page is the one that I tried to link from and the one that I downloaded the driver from. But I can't get this to work:
Code:

sh NVIDIA-Linux-x86-1.0-8174-pkg1.run


Try:

```
sudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
```

---

### Post by kc5hwb on 2007-04-08
Got the same error telling me that X is already running and they recommend that I don't install this while X is running.

---

### Post by kc5hwb on 2007-04-08
```
sudo nano /etc/X11/xorg.conf
```

I ran this command and changed the drivers to "nvidia" and rebooted, and it still won't load X, it just comes up to a black screen.  So I changed it back to "vesa" 

And I tried running the sh command with sudo, but it doesn't want to install with X running.

---

### Post by mikewhatever on 2007-04-08
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)
 [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

I haven't had the time to read through this long long thread, but think it should be useful to all who try installing their nvidia drivers manually.

---

### Post by kyphi on 2007-04-09
After installing nvidia-glx you need to enable it.

sudo nvidia-glx-config enable

Then log out and back in again.

That is the correct driver for your card.

---

### Post by kc5hwb on 2007-04-09
k, trying that now.

---

### Post by kc5hwb on 2007-04-09
do you know what driver it IS in Synaptic?  Someone else on the Nvidia site told me I should be using 1.0-9755.  We'll see I guess.

---

### Post by kyphi on 2007-04-09
I have used this driver for a GeForce 5200, 5600, 6600 and a 7900 card.    Since this driver has always worked for me I can see no reason to change it.

In Synaptic it is identified as nvidia-glx 1.0.8776.  Originally I downloaded it via Automatix.

---

### Post by kc5hwb on 2007-04-09
Didn't work............


I ran the command you gave me, rebooted and X would not load......it came up to a blacnk, black screen, the same way it did before.

---

### Post by kc5hwb on 2007-04-09
> **kyphi said:**
> After installing nvidia-glx you need to enable it.

sudo nvidia-glx-config enable

Then log out and back in again.

That is the correct driver for your card.

This is the result of running that command
> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

---

### Post by aktiwers on 2007-04-09
I always use this
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Very easy!

---

### Post by kyphi on 2007-04-09
If nvidia-glx has been enabled and presents problems, you may need to restore the backed-up config file first.

cp /var/backups/xorg/xorg.conf.2007-04-10- 99:99:99 /etc/X11/xorg.conf

Check the directory .var/backups/xorg first to correctly identify the filename.  Where I have put "99:99:99" you need to remove that and insert the time stated on the backed up file.

The solution offered by aktiwers may very well be the easiest.

---

### Post by kc5hwb on 2007-04-10
> **aktiwers said:**
> I always use this
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Very easy!

I can't seem to win for losing....


> Ubuntu Edgy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.                    this might happen because either your card is not supported by the driver or Envy's hardware                    detection failed. You can try the manual installation at your risk.

---

### Post by kyphi on 2007-04-10
Sorry to read that you have had no success.

According to [http://phoronix.com/vr.php?view=6419](http://phoronix.com/vr.php?view=6419)
the driver for the 6100 chip is 1.0.8756

Ubuntu.com/HardwareSupport under Graphics Cards, Integrated Series 6000 has some good instructions but as far as I could see these were for Dapper.  Read them anyway.

If you have a desktop PC you could follow the more drastic path of installing a supported graphics card and disabling the inbuilt chip.  I have done that in my present system for both graphics and sound.

---

### Post by kc5hwb on 2007-04-10
Honestly I thought about that.  It seems like a waste since the GeForce 6100 seems like such a good card.  Do you think that Linux will develop a working driver some time down the road if I do this as a temporary solution for now?

---

### Post by kyphi on 2007-04-11
I could not forecast what may happen regarding a compatibility for inbuilt chips.  Please remember that the 6100 is not a graphics card but rather an inbuilt chip on a motherboard (like a winmodem).

I think Ubuntu is the best thing since sliced bread was invented.  How much Ubuntu means to you will determine to what length you would go to get it working or to keep it working.

I had a number of compatibility issues during the transition from XP to Ubuntu.  The last one remaining is my Canon scanner.  It would seem that to resolve that I will have to bin my perfectly good scanner and buy an Ubuntu compatible scanner.

The issue of XP software programmes I just could not do without were solved by adopting Codeweaver's CrossOver Linux.

The only purposes that I have for XP now is access to 3 small games, PhotoImpact and Morrowind and Oblivion and the scanner.  I have nobbled XP so that it has no internet connection and therefore does not present a security threat, which also means that I do not need a commercial Virus Scanner.

In my most recent computer build I jumped too far ahead and had some compatibility problems but most of these have now been resolved.

The easiest solution for you, as mentioned before, is to disable your inbuilt graphics chip and install a compatible graphics card.

Alternatively, use Ubuntu 6.06, which may work or be very patient until the issue is resolved.

I am not going to abandon you in your plight, if you wish, you could leave me a private message with your contact details and I promise to respond.

---

### Post by championboxes on 2007-04-19
you might be able to install the drivers if you change the run level to 3 type "nano /etc/inittab"  then change it to 3... i dont know if it will work in ubuntu but i do know that it works with fedora...  o yeah when you boot you need to type "startx" to start the x server

---

### Post by Wim Sturkenboom on 2007-04-19
I will check tonight as I have it working on my Dapper Drake. I followed the first method on [http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264) ; there is a similar page for 6.10

Can somebody tell me how I find the version of the driver that I installed so I don't have to spend a few hours trying to find that out?

---

### Post by kc5hwb on 2007-04-19
Thanks guys, I got this working based on some info from the nvidia forums.

---

### Post by Slade Winstone on 2007-04-20
Please feel free to share the info that you got from the nvidia forums, for those of us who had a working 6100 install that got screwed up with the upgrade to Fesity :(

Thanks,
Slade.

---

