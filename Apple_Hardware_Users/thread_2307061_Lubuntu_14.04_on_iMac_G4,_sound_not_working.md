---
title: "Lubuntu 14.04 on iMac G4, sound not working"
date: 2015-12-21
forum: Apple Hardware Users
---

### Post by gsn313 on 2015-12-21
Installed Lubuntu 14.04 on my iMac G4, and the speed of this OS is great . However, while playing youtube videos, only the video works. I've tried to get sound with an html5 audio test, but still no sound. I've come to the conclusion that there's **n****o audio functionality with this Lubuntu 14.04 on my iMac**. Also, the gnome mplayer wouldn't play my cd's or dvd's. Would love to get this setup to work. Thanks!

---

### Post by SlidingHorn on 2015-12-21
The most common answer I see on askubuntu seems to be to install pavucontrol:

```
sudo apt-get install pavucontrol
```

In terminal run [FONT=Courier New]pavucontrol[/FONT]

1. In Configuration tab for Built-In Audio
[INDENT]
Profile : Analog

Make sure HDMI is not selected.[/INDENT]

2. Make sure volume is set in all other tabs of pavucontrol

Source:  [http://askubuntu.com/questions/493738/no-sound-in-lubuntu-14-04](http://askubuntu.com/questions/493738/no-sound-in-lubuntu-14-04)  which leads to [http://askubuntu.com/questions/267531/lubuntu-no-sound-at-all-no-mute-alsa-pulse](http://askubuntu.com/questions/267531/lubuntu-no-sound-at-all-no-mute-alsa-pulse)

---

### Post by gsn313 on 2015-12-21
Ok so I did everythng listed, But in the configuration tab of pavucontrol there's a message: "No cards avaiable for configuration." What should I do now? Thanks again btw!

---

### Post by SlidingHorn on 2015-12-21
That's interesting....  what's the output of the following command (if you could, please place in code tags)

```
sudo lshw -c sound
```

---

### Post by howefield on 2015-12-21
Thread moved to the "*Apple Hardware Users*" forum for better support.

---

### Post by gsn313 on 2015-12-21
Super sorry, I don't know how to use code tags. Is that an html thing? Anyway I ran the code in the terminal and the output was: "PCI (sysfs)" What should I do now?

---

### Post by SlidingHorn on 2015-12-21
No worries :)  Here's a quick run down on how to use [code] tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by gsn313 on 2015-12-21
Aha! Thanks! So my output code is...


```

[COLOR=#000080]PCI (sysfs) [/COLOR]

```

What does this mean? What steps should I take now? Thanks again!

---

### Post by rough68fish on 2015-12-21
I just got this working on my 1.25Mhz 20" iMac Lamp with 14.04 and KDE. I could see in dmesg that the snd_powermac module was being loaded so I commented that out in /etc/modules and added:

snd-aoa
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-fabric-layout
[COLOR=#111111][FONT=Consolas]snd-aoa-codec-tas[/FONT][/COLOR]

rebooted

Then I started alsamixer (it wouldn't start when snd_powermac was loaded and snd-aoa was't) unmuted and turned everything up and I had sound. I don't have speakers for mine so it is just using the internal speaker.

I didn't mess with the blacklist I just confirmed that the snd-aoa stuff wasn't being blacklisted.

See the second answer here:
[http://askubuntu.com/questions/397705/no-sound-on-powerpc-soundcard-not-detected](http://askubuntu.com/questions/397705/no-sound-on-powerpc-soundcard-not-detected)

---

### Post by gsn313 on 2015-12-21
Awesome! Thanks for the help! So I went to /etc in the file manager and I only see modules-load.d, and inside of there is something called "cups-filters.conf" which has all of this in it:

 # Parallel printer driver modules loading for cups
# LOAD_LP_MODULE was 'yes' in /etc/default/cups
lp
ppdev
parport_pc


There isn't a snd_powermac to comment out, so I'm thinking this is the wrong location. Am I right?

---

### Post by rough68fish on 2015-12-22
> **gsn313 said:**
> Awesome! Thanks for the help! So I went to /etc in the file manager and I only see modules-load.d, and inside of there is something called "cups-filters.conf" which has all of this in it:

 # Parallel printer driver modules loading for cups
# LOAD_LP_MODULE was 'yes' in /etc/default/cups
lp
ppdev
parport_pc


There isn't a snd_powermac to comment out, so I'm thinking this is the wrong location. Am I right?

That's not the right file. Cups is for printing services.

it should be just /etc/modules. Maybe file manager hides it from you like windows since your normal user account probably doesn't have rights to it. 

Open a terminal and try 

```

ls -la /etc/modules

```

Then you should see the file. Then you can edit it with nano.

```

sudo cp /etc/modules /etc/modules.orig
sudo nano /etc/modules

```

You should be prompted for your password to "elevate" your rights to root for he commands.

---

