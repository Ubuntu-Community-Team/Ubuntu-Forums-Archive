---
title: "Ubuntu noob- jerky 3d games"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Tylazene on 2008-01-20
Hi all, newly moved over to Ubuntu hoping to forget windows exists. I think it's great that you guys are here to help so many people. I wanted to try out some of the linux 3d games (like Nexuis) but the frame rate must be like 5 or 6. Makes playing impossible. Even the 3d screensaver is jerky. I'm guessing it's probably the driver? It's only onboard video but I can play BF 1942 on XP at mid settings no prob. What gives?

Here's my specs:

Gutsy 7.10
2.5 gig Intel Celeron
700 mb  ram 
Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device 
Hauppuage pvr150
Creative Soundblaster live! sound card

I think device manager says it's using i810 smbus driver now (whatever that is). BTW, I'm a total noob to linux and not great with command line so I might need things spelled out for me :)

Thanks,

Ty

---

### Post by NovaAesa on 2008-01-20
Go into System -> administration -> restricted drivers and enable the restricted drivers. Post back with what happens (you may have to restart for any effect to take place, but I'm not sure on that one).

---

### Post by SOULRiDER on 2008-01-20
If you have desktop effects enabled disable them wheny ou go to play and then re enable them if you want after youre done.

---

### Post by st33med on 2008-01-20
Let me tell you this: Intel Integrated cads suck hard. I get almost the same thing with an Intel 945GMA. Seriously, if you somehow get it above 20 fps on average, I would congratulate you. Not to mention that I would like to know how :)

If you want to replace the graphics card, it is integrated into the motherboard, so, you would need to replace the motherboard.

Sorry if that was not much help :\

---

### Post by Pethegreat on 2008-01-20
> **st33med said:**
> Let me tell you this: Intel Integrated cads suck hard. I get almost the same thing with an Intel 945GMA. Seriously, if you somehow get it above 20 fps on average, I would congratulate you. Not to mention that I would like to know how :)

If you want to replace the graphics card, it is integrated into the motherboard, so, you would need to replace the motherboard.

Sorry if that was not much help :\

From what he has said, integrated video has gotten better over time(I would never be able to run anything good on my old intel card). He should be hitting better frame rates since Ubuntu does not eat resources like XP. I also think that Nexuis should be less demanding than Bf1942 on a video card since there is less to render in the screen. 

I have a similar problem to his with a X1650. I am still wondering if I should take it on.

---

### Post by Tylazene on 2008-01-20
Checked restricted drivers. Said none were needed but I restarted anyway. Desktop effects off. I heard somewhere that I should get an accelerated 3d driver? From where?

---

### Post by st33med on 2008-01-20
> **Pethegreat said:**
> From what he has said, integrated video has gotten better over time(I would never be able to run anything good on my old intel card). He should be hitting better frame rates since Ubuntu does not eat resources like XP. I also think that Nexuis should be less demanding than Bf1942 on a video card since there is less to render in the screen. 

I have a similar problem to his with a X1650. I am still wondering if I should take it on.

Well, he has a really old Intel GPU. GM/GMA's are the current chipsets (I think)

> **Tylazene said:**
> Checked restricted drivers. Said none were needed but I restarted anyway. Desktop effects off. I heard somewhere that I should get an accelerated 3d driver? From where?

There are no restricted drivers necessary. Could you post the output of:
```
cat /etc/X11/xorg.conf | grep Driver
```

EDIT: Yes, he has an old chipset. It is about six years old... Wow.

---

### Post by smartboyathome on 2008-01-20
I think the problem is that the i810 driver is currently borked (I can't get it to run at all on my Intel GMA 945 machine). I can't play 3D games on that comp either, and that is using intel's experimental drivers. They pretty much crash my xserver.

---

### Post by Tylazene on 2008-01-20
cat /etc/X11/xorg.conf | grep Driver:


        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "i810"

Up until now I haven't had a need for a new MB. :confused:

---

### Post by st33med on 2008-01-20
You could try the experimental 'intel' driver for your chipset. You just need open xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```

And find the line which says:

```
Driver "i810"
```

Before you replace the i810, check to see if you have the intel driver:
```
sudo apt-get install xserver-xorg-video-intel
```

If your system does not have it, it will install it. Now, replace the "i810" in xorg.conf with "intel". Reboot. It might be better, but, who knows.

---

### Post by Tylazene on 2008-01-20
I checked, it IS the i810 driver. Ran that code but says it already has the newest driver. But.... I searched Intel's site and found the i915 driver for my chipset. I downloaded it in a tar file but what do I do with it???

Thanks for the help

---

### Post by st33med on 2008-01-20
That driver is not yet supported by Xorg. Don't do anything with it.

As I said, replace the line:
```
Driver "i810"
```
in /etc/X11/xorg.cong with:
```
Driver "intel"
```

---

### Post by Faud on 2008-01-20
> **st33med said:**
> Let me tell you this: Intel Integrated cads suck hard. I get almost the same thing with an Intel 945GMA. Seriously, if you somehow get it above 20 fps on average, I would congratulate you. Not to mention that I would like to know how :)

If you want to replace the graphics card, it is integrated into the motherboard, so, you would need to replace the motherboard.

Sorry if that was not much help :\
Wouldnt it be possible for the OP ( if the want ) to disable their graphics card in the bios and set it to PCI ?

---

### Post by Tylazene on 2008-01-20
Ok that seemed to help some. When playing Nexuis3d the framerate REALLY slows down when there is another artificial intelligence in the same room (gets A LOT worse with 2). Otherwise I can zoom though a room really fast. Now I'm thinking something with the CPU.

---

