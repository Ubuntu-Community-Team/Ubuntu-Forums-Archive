---
title: "Giving up on Nvidia in Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dmsynck on 2007-04-24
Well, after having tried the following Nvidia drivers from the repos - 

"New" , 
"New Legacy", 
"Legacy"

And having also tried both Envy and Automatix. I have yet to find anything that will make the nvidia drivers and the X server work together without errors. Going back to good ol "nv" for now. Maybe I will try again with the next release. I really had high hopes that nvidia would work without a lot of hassle this go around.

---

### Post by phidia on 2007-04-24
I have a GeForce FX5500 gpu and it works with feisty. With the beta release I had to manually install the nvidia driver but now that feisty is officially final it works with the nvidi-glx-new driver.

What errors did you get? Have you checked in the multimedia & video section here?

[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by DJ_Peng on 2007-04-25
I've got Feisty running on my Nvidia GeForce2 MX 100, and I see a lot of people are enjoying Feisty on Nvidia graphics cards. Which card do you have? Thats' actually one of the first things to find out to get Nvidia working because different cards use different drivers, and even different builds can force a change in what drivers to use.

---

### Post by iPirates on 2007-04-25
Yea, I tried using an nVidia 8600 gts on fiesty, and could not get it working for the life of me.  Then I realized that nVidia only just released the drivers for it, and they're still in the "beta" version.  So it depends on what card you're trying to get working.  I've slapped my 6600 gt oc back in for now, gonna return the 8600 for an 8800, which has full support. 

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

Check out if your card is supported (more specifically on the nvidia site).

---

### Post by Patrick K on 2007-04-25
Did you try installing it using System>Administration>Restricted Drivers Manager? I did and everything works great with my Geforce2 MX 200 card.

---

### Post by SeanWuzHere on 2007-04-25
I have a NVIDIA FX 5700 Ultra card. This link below kinda/sorta worked for me. I just used this "Alberto Milones Envy program".

link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

That said,.. it works but there is still a problem. When I reboot,.. the screen defaults back to 1024x768 when I log in. So I go to Applications>System Tools>NVIDIA Settings and set it there. Then I tell it to save the settings to /etc/X11/xorg.conf file. Which it seems to do but upon further investigation it clearly does not. So I have to do it manually.

So I save a backup of my original xorg.conf file,... replace the contents of it with the text from the NVIDIA Settings tool and now upon a reboot my settings are saved. Hooray! But now another problem. If I have System>Preferences>Desktop Effects (I.e. wobbly windows) enabled, then all the windows launch as frozen unmoveable windows. Like I can open Firefox or a terminal or whatever, and I can even use these programs,.. I just can't move these windows around or resize them. But if I turn off wobbly windows then all the problems are go away.

So yeah, definitely lots of driver bugs still happening.

Anyway, just my 2 cents. :)

---

### Post by igknighted on 2007-04-25
I would bet that trying to install so many times might be part of your issue.  If pieces were left over then there might be conflicts.  I would try a fresh install and post your card on here and we can point you to the proper one the first time.

---

### Post by Billium on 2007-04-25
I have a 5160 LE and was having all sorts of trouble.

I used the ENVY program and everything is working just fine now.

Choices of many different resolutions. Although the restricted drivers manager says it's not supported, it really works fine.

---

### Post by jcrow on 2007-04-25
I am  new to Ubuntu, but I had installed Fiesty to be able to use Compiz and I too had all sorts of problems with screen resolution with the legacy drivers. I did some research on the video card I had (riva tnt2) and found out it is really old. Since I didn't think it would work very well with Compiz or Beryl, I decided to pick up an inexpensive card. I picked up a Nvidia 5200 AGP card for around $60 and dropped it in. I configured it in XP (my wife fears change) and had to go through several restarts and configuration settings. Once that was done, I restarted in Ubuntu and the screen resolution was good. I went into the restrictive driver settings and installed the Nvidia driver and restarted. On the restart, I enabled the desktop effects and everything seems to work. I think it was way easier to set up the card in Ubuntu than XP. The only thing I noticed was that Firefox seems to freeze while loading a page in a new tab. I wonder if the desktop effects are bogging the machine down or if it has something to the pipelining settings I changed.

---

### Post by dmsynck on 2007-04-25
Here is the relevant section from running sudo lshw -

```

*-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: c1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
                resources: iomemory:fd000000-fdffffff iomemory:e8000000-efffffff

```

This is on Kubuntu 7.04.
Any ideas on which Nvidia driver I should be trying to use and is it better to install driver through "Envy" ?

---

### Post by BOZG on 2007-04-25
> **iPirates said:**
> Yea, I tried using an nVidia 8600 gts on fiesty, and could not get it working for the life of me.  Then I realized that nVidia only just released the drivers for it, and they're still in the "beta" version.  So it depends on what card you're trying to get working.  I've slapped my 6600 gt oc back in for now, gonna return the 8600 for an 8800, which has full support. 

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

Check out if your card is supported (more specifically on the nvidia site).

I'm trying to install an 8800GTS at the moment and it will not work at all.

---

### Post by J11Gyro on 2007-04-25
Just for the heck of it have you tried automatix2?

---

### Post by Billium on 2007-04-25
Like I said earlier, ENVY worked really well for me. 
Even with the restricted drivers my resolution is good, and this system has not crashed once.
Now I need to learn all the little extras. Desktop and such.

Good luck

---

### Post by iPirates on 2007-04-25
> **BOZG said:**
> I'm trying to install an 8800GTS at the moment and it will not work at all.

Have you tried installing the drivers with Envy??

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It's worked for all the other cards i've had to install (not the 8600 of course, because there's no support for it yet)

---

### Post by et voilà on 2007-04-26
I have a similar problem with a Geforce4 MX. 

xorg cannot start with the binaries compiled by Envy or with those gotten on Synaptic (nvidia-glx, 9631). 

Via the menu Adminitration, it only changes the .conf with nvidia driver instead of nv and it adds ARGBVisuals in options, so no go, xorg does not start.

This was not a problem in Edgy with the same hardware. 

FYI I did upgrade from Edgy to Feisty with update manager, if that could help figure the problem. I was expecting the upgrade would break xorg, but I though a dpkg-reconfigure xserver-xorg in terminal would fix all problems relative to Feisty.

Ciao

---

### Post by iPirates on 2007-04-27
I duno if this is acurate, but i heard that once you do an upgrade, you have to reinstall your video drivers manually (as if you had just installed feisty from a cd)....
this is just a reflection of something i think i read somewhere stored in my memory, so i'm not 100%

---

### Post by PartisanEntity on 2007-04-27
> **iPirates said:**
> I duno if this is acurate, but i heard that once you do an upgrade, you have to reinstall your video drivers manually (as if you had just installed feisty from a cd)....
this is just a reflection of something i think i read somewhere stored in my memory, so i'm not 100%

Didn't apply to my case, in Edgy I had used Envy to install the latest Nvidia drivers for my Geforce Go 6200. Then I upgraded to Feisty and everything was working, including the drivers I had installed in Edgy. In fact the funny thing is that now the update manager keeps informing me that an update for my graphics card is available, but of course the drivers in the repo are older than the ones I have installed, so I ignore it.

---

### Post by iPirates on 2007-04-27
**EDIT whoops double post....

---

### Post by u.b.u.n.t.u on 2007-04-27
Xorg 7.3 is scheduled to be released in May, so that is of interest as a possible fix.

---

### Post by orb9220 on 2007-04-27
> I duno if this is acurate, but i heard that once you do an upgrade, you have to reinstall your video drivers manually 

Well I had an update break x so I was sitting there at the command prompt. Then I remembered that I had envy installed. So I just typed envy and boom it did it's magic and then I was good to go.

---

### Post by iPirates on 2007-04-27
> **u.b.u.n.t.u said:**
> Xorg 7.3 is scheduled to be released in May, so that is of interest as a possible fix.

yea and nVidia is releasing new drivers, with added support of new cards too,  in May...

---

### Post by jack888 on 2007-04-29
[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)
Success! Compiling Nvidia 8776 driver on Feisty 2.6.20-xx-386

I have a nvidia quadro4 980 and I also have tried all kinds of solutions.
After upgrade to feisty , nvidia was working but with no GL.

I followed the instructions in the above link and when I tried to start X it still failed but
it was still trying to load nvidia kernel module from /lib/modules/2.6.20-15-386/volatile.

The one that I compiled from the above instructions was here
/lib/modules/2.6.20-15-386/kernel/drivers/video/nvidia.ko

So I did insmod /lib/modules/2.6.20-15-386/kernel/drivers/video/nvidia.ko
Then X was working again.
This all started because I was trying to get Beryl working again which it is.

I find sometimes it is a combination of solutions which solves the problem.

hope this helps


Remember wherever you go there you are.

---

### Post by sites on 2007-04-29
How does one enable the restricted drivers in Kubuntu? All the tips i find are using Gnome.

---

### Post by sites on 2007-04-29
GOT IT now..... just have to do it the old way i guess.

$ sudo apt-get install nvidia-glx nvidia-kernel-common
$ sudo nvidia-xconfig
Ctrl+Alt+Backspace

:guitar:

---

### Post by Lex Luthor on 2007-06-08
> **DJ_Peng said:**
> I've got Feisty running on my Nvidia GeForce2 MX 100, and I see a lot of people are enjoying Feisty on Nvidia graphics cards. Which card do you have? Thats' actually one of the first things to find out to get Nvidia working because different cards use different drivers, and even different builds can force a change in what drivers to use.

But did you get it to work with Compiz ?
I got it to work with compiz in Dapper, with all those great animations. This week I tried to make it work on Feisty, but I couldn't make it work.

First I installed from Restrict Drivers Manager, it installed nvidia-glx. It didn't work. 
So I installed nvidia-glx-legacy (nvidia-glx-new does not work either), and got to start X server, but Compiz does not work, it refuses to animate my windows. 
Typing glxinfo I get a lot of errors saying GLX is not enabled.

I have a NVidia Geforce2 MX 200 with 64Mb Ram, no TVOut.

I don't know what else to do.

---

