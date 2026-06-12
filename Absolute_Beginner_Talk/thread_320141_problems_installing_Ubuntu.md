---
title: "problems installing Ubuntu"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-16
Hi
Once again I got problems installing Ubuntu, when I first tried it started loading the LiveCD, but it came to a point where the screen just turned all to black an a message appeared, it said "sinc. out of limit", so I was told to download the alternate version of Ubuntu.
I downloaded it and I was able to install it on Text mode, but when the computer restarted, the problem appeared again, the Ubuntu symbol was too clear, and it is more difficult to see, when it finishes loading the "sinc. out of limit" message appears again, the monitor seems like if it was disconnected and I could hear a noise, but I can't see anything.
I pressed Ctrl+Alt+F4 and a new scree appeared, it said something about log in with the user I created, I entered the password and another line appeared saying password, in the password line I tried to type my password and I couldn't even write there. 
What do I need to do to have my Ubuntu installed without problems?:confused:

---

### Post by Bachstelze on 2006-12-16
Seems you're using a resolution and/or refresh rate that your monitor can't support.

When you login from the command line you *can* type. You don't see anything when you type your password for security reasons, it's normal - if someone knows the number of cheracters in your password, it's more than half the job done for cracking it. Just type your password and press enter. Then, when you're at the command prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you a bunch of questions, if you don't know what to answer, stick with the defaults. It will also let you choose the resolution you want to use, pick one your monitor supports and you will be fine.

---

### Post by Jorge32 on 2006-12-16
ok, I already did it, and now what? it appears the line waiting for another command after reconfiguring xserver-xorg, What do I need to type there?

---

### Post by Bachstelze on 2006-12-16
```
sudo /etc/init.d/gdm start
```

Will attempt to start the X server again. It you are told it's already running, put restart instead of start.

---

### Post by Jorge32 on 2006-12-16
I already did it! and the message "sinc out of limit", well exactly it says "sinc. fuera límite" in spanish, The point is that nothing happens! anything else for me to do?

---

### Post by Bachstelze on 2006-12-16
Well, if you already did all of that, you should have told as I have poor Divination skills... Anyway, what resolution did you try and are you sure your monitor supports it ?

---

### Post by Jorge32 on 2006-12-16
Yes, it is the resolution that I usally saw my monitor uses, but anyway, I'll tray again changing some resolutions, do I need to change something about the monitor in configuraton xserver-xorg?

---

### Post by Nopposan on 2006-12-16
I'm not familiar with the solution given but I've tried using a DSL (damn small Linux) cd to edit my /etc/xorg.conf file.  That worked for me.

You've already installed, right?

Did you have trouble using the graphical installer?  Did you have to use the "Alternate CD?"  I did, because my screen's color depth is only 16 bit, not 24 which is the default.  'Could be it's your color depth and not your resolution that's the problem.  'Could also be the refresh rate.

Anyway, it's key to learn as much as you can about how your monitor is meant to be run; if you don't already have all of the specifications then you can try your computer manufacturer's website or a popular internet search engine.  Then again, you can just backup the xorg.conf file and then start changing things until something works; I learned about my screen by trying out different configurations on a live cd that wouldn't work right until I got the configuration right.

My message to you is that no matter how long it takes to get your screen to display correctly, you will eventually do it.  You know your resolution so that means you're probably more than halfway there.  Your tenacity will win this scenario even if education and help from us doesn't.

Cheers.

---

### Post by Jorge32 on 2006-12-16
I had tried a lot of different configurations, if this helps my monitor is a Samsung SyncMaster 551v, and my video card is a Matrox MGA G200 AGP.
The message "Sync Out of Range" moving around the black screen keeps on appearing, and I tried to configure the xserver xorg with various configurations in depth and resolution.
By the way, yes I used an alternate Ubuntu CD, running the text mode install.
I've read about something called x11 configuration or something like, with the same monitor in another version of linux installation. Does it has to do with this also? :confused: :confused: :confused:

---

### Post by Nopposan on 2006-12-18
You're in luck.  Not all manufacturers are so generous, but here's some information from the free pdf manual from Samsung:

"Judging the monitor's working condition
If there is no image on the screen or an "Sync. Out of Range" message comes up, disconnect the cable from the computer while the monitor is still powered on.
If there is a message coming up on the screen or if the screen goes white, this means the monitor is in working condition.
In this case, check the computer for trouble."

Specifications
User’s Manual
General
Model Name SyncMaster 551v
Picture Tube
Type 15"(38cm) Full square type (35cm viewable)
Deflection angle 90°
Dot Pitch 0.24mm(Horizontal)
Screen type Aluminized tri-color phosphor dot trio with black matrix.
Anti-doming invar shadow mask.Glare/ESF.
Maximum Resolution
1024 Dots, 768 Lines @68Hz
Active Display
Horizontal 267 ± 4 mm
Vertical 200 ± 4 mm
Synchronization
Horizontal 30 ~ 55 kHz
Vertical 50 ~ 120 Hz
Input Signal Definition
Video Signal RGB, Analog 0.7 Vpp positive at 75 ohms
Sync Signal separate H/V sync, TTL level, positive or negative
Display Color
Unlimited
Maximum Pixel Clock
65MHz
Power Supply
90 ~ 264VAC rms, 60/50 Hz ± 3Hz
Power Consumption
80 W(Max.), 70 W(Nom.)
Dimensions (WxDxH)
356x 380 x 369.5mm (with stand)
Weight
11.5 kg
Environmental Considerations
Operating Temperature 32 F ~ 104 F (0 ~ 40 )
Humidity 10% ~ 80%, non-condensing
Storage Temperature -4 F ~ 113 F (-20 ~ -45 )
Humidity 5% ~ 95%, non-condensing
Plug and Play Capability
This monitor can be installed on any Plug & Play compatible system. Interaction of the monitor and computer systems will provide the best operating conditions and monitor settings. In most cases, monitor installation will proceed automatically, unless the user wishes to select alternate settings."

So, pay attention to the horizontal and vertical synchronization, the resolution, and the frequency (Hz).  It's all there.  Also, you can test your monitor to see if it's still working.

Let us know how it goes.

---

### Post by Nopposan on 2006-12-19
1024 Dots, 768 Lines @68Hz

That means your /etc/X11/xorg.conf file should have a line that looks something like:

1024x768@68

. . . instead of whatever's there now.  Also, be sure the horizontal and vertical synchronizations are set to the specifications listed.

Samsung's website has the complete pdf manual for your monitor available as a free download.  There's a Spanish language version as well.

Unless something's wrong with your monitor or video card, I think you'll be able to get it working under Linux.

Happy tweaking.

---

