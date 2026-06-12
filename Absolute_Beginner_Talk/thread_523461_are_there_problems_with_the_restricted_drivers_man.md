---
title: "are there problems with the restricted drivers manager?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-08-11
I am just about ready to install a Tornado Geforce FX 5200 (Inno 3D). (Graphic Controller Nvidia GeForce FX 5200). 
Motherboard Asus P5vdc-mx. Celeron 1.6 G. Ubuntu Feisty Fawn.
I recently installed NVIDIA drivers with the Restricted Drivers Managers on an old Pentium $ 1.5 Gig computer and now cannot get any higher screen resolution then 800 x 600. (A problem that I will tackle at another time. I have seen the posts dealing with how to fix this and they are a bit above my head to be honest.)
I would like to know what the best way is to install NVIDIA drivers. Is there a problem with the installer that comes with Feisty? I also heard about a program called Envy. Could somebody please point me into the right direction.
This is for a friend I would like to convert to Linux. Unfortunately I do not have the time to spend hours on fixing problems and only have a _very _limited knowledge of the command line.:(
Thank you :)

---

### Post by starcraft.man on 2007-08-11
[Envy.]("http://albertomilone.com/nvidia_scripts1.html") Instructions on the page. I prefer Envy myself.

As for the resolution error, bleh I see that often. Usually it's just a problem when the xorg was reconfigured. Two easy solutions, first is to paste your xorg here for me to edit (then you paste it over the old). Second is to fix it via the automatic command.

1) Open a terminal (Applications > Accessories > Terminal) and paste this in:

```
gksudo gedit /etc/X11/xorg.conf
```

then paste the entire file here and I'll edit in the modelines. Then copy and paste it back in the file and save it out over the old.

2) Open same terminal and paste in :

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the screens carefully and when in doubt push ok and don't modify. When you get to resolutions screen pick your monitors maximum.

In both cases a simple restart will then apply the new settings after saved without trouble (or if you don't want to restart just push ctrl + alt + backspace for a GDM restart). Be sure nothing you want to lose is open.

To answer the main questions, no there aren't really any problems with restricted driver management itself (least not in my experience).

---

### Post by overdrank on 2007-08-11
> **Chamelion said:**
> I am just about ready to install a Tornado Geforce FX 5200 (Inno 3D). (Graphic Controller Nvidia GeForce FX 5200). 
Motherboard Asus P5vdc-mx. Celeron 1.6 G. Ubuntu Feisty Fawn.
I recently installed NVIDIA drivers with the Restricted Drivers Managers on an old Pentium $ 1.5 Gig computer and now cannot get any higher screen resolution then 800 x 600. (A problem that I will tackle at another time. I have seen the posts dealing with how to fix this and they are a bit above my head to be honest.)
I would like to know what the best way is to install NVIDIA drivers. Is there a problem with the installer that comes with Feisty? I also heard about a program called Envy. Could somebody please point me into the right direction.
This is for a friend I would like to convert to Linux. Unfortunately I do not have the time to spend hours on fixing problems and only have a _very _limited knowledge of the command line.:(
Thank you :)

HI this thread may help with the Geforce card and it is envy.
[http://ubuntuforums.org/showthread.php?t=432056&highlight=Geforce+FX+5200](http://ubuntuforums.org/showthread.php?t=432056&highlight=Geforce+FX+5200)

:guitar:

---

### Post by RomeReactor on 2007-08-11
Hi. I don't think there's any problem with installing the drivers through Synaptic, though your mileage may vary. In my case it's always worked. Take a look at my post in [this thread ]("http://ubuntuforums.org/showthread.php?p=3172076#post3172076")for an easy way to get 3D rendering with your GeForce, and [this other post]("http://ubuntuforums.org/showthread.php?p=3172923#post3172923") to see if you can change your resolution.

EDIT: Too slow...

---

### Post by Chamelion on 2007-08-12
OK, I have installed the thing. I forgot to say that I am dual booting with Windows XP. There was not any problems installing on the XP drive. All seems to be working fine too.
Unfortunately I did not get round to install the NVidia drives onto the Ubuntu drive because I cannot get into the Ubuntu drive anymore.
The start up screen giving me the choice of Ubuntu and XP is still there. When I choose Ubuntu the boot screen comes up. The orange line manages to get all the way to the right too. Then the monitor turns black.
I tried to start Ubuntu in safe mode. Shortly after typing startx the monitor turns black again.
I just noticed that the Memory Configuration info of the graphics card says: 64/128MB DDR Memory.
Could there be a problem with my Ubuntu version? (32bit)
Please remember my knowledge of all of this is still very little.
I really would appreciate your help.
Thanx again

---

### Post by starcraft.man on 2007-08-12
Har! Ok then, seems like a lil problem, no biggie. Firstly no there isn't a problem with the version of Ubuntu. The memory on the card (64/128) listed is the total amount of VRAM in it, that's how much it can cache while rendering. The card should be fine (assuming it works in Windows).

Now as for fixing the problem, should be simple. Reboot and drop into the recovery console from the safe mode option (it should be second boot option). When you get there and are at the prompt please type the following in:

```
sudo dpkg-reconfigure xserver-xorg
```

This will take you through a series of screens that will allow you to graphically reconfigure the xorg (it is what controls configuration of your display, card and peripherals...). Follow the screens and use tab + arrow keys to move around, enter to select and stick to the default when in doubt. When you get to the choose driver page for your video card make sure it's set to "vesa", it will be in the list. Continue through the screens and when you get to the end it will save upon exit. 

Then do just restart the computer and boot up normally or use any of the commands available (like "startx") to start the GDM. That should do it. After, log in and follow the instructions for installing envy.

Best of luck with the new card :).

Oh and sorry it took 14 hours for someone to answer >.>.

---

### Post by misfitpierce on 2007-08-12
Envy worked great for me... I have ATI tho but it installs Nvidia too. Great program.

---

### Post by Chamelion on 2007-08-12
I have tried to reconfigure 3 times now. With a few variations just in case I did something wrong.
The monitor still turns black. It actually seems to turn of. I can hear Ubuntu starting.
:confused::(

---

