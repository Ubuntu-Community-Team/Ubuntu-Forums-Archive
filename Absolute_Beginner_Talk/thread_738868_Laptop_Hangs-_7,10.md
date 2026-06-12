---
title: "Laptop Hangs- 7,10"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Jaems on 2008-03-29
Hey,
Posted this in the laptop section 4-5 days ago and got not much back except someone else with the same problem.

Give or take some mistakes, it said this-

 I recently installed 7.10 (Ubuntu Studio) onto my new laptop. There were some installation issues, but they are mostly sorted (the internal speakers don't make a sound, but i'm not too worried.)

The problem i have now is that certain operations make the computer hang horribly. The main culptrits are update manager (when it begins updating) and when the 'you have chosen to open' dialog (open with/save to disk) in firefox.

The mouse moves as if it is being refreshed at 1 fps and NOTHING responds- Mouse clicks, keyboard macros, function buttons. The laptop's LEDs show no CPU or HDD activity. If i leave it for 20 minutes, everything has disappeared save the desktop background. The story invariably ends with me holding down the power button.

The only related issues from the install that i think could be linked are
- Gnome settings daemon gave an error at startup the first few boots. I set it to run in sessions and it hasn't complained since.
- The Wireless driver was very troublesome to install. At the moment it is running on the .inf i ripped from the vista partition in Ndiswrapper.
-It gives a 'failed to load memory resourse 00' etc. etc. (moves really fast before the splash screen so is hard to catch, but looks like an IRQ address or some sort of hardware thing.

The laptop is a Core Duo 1.66 with an Nvidia 8600GS and 3 gb ram. Everything else seems to work fine. I've tried the Nvidia-settings new, nvidia-settings and at the moment am running on the nv driver.

Any ideas?? The old thread can be found

Here- [http://ubuntuforums.org/showthread.php?t=733527](http://ubuntuforums.org/showthread.php?t=733527)

---

### Post by ramjet_1953 on 2008-03-29
Try this to see what is going on:

Install the system monitor applet on you taskbar and when things start to go crazy, left click on the applet.Hopefully, there will still be enough memory / CPU capacity still remaining, to see what is going on as it will list all tasks running, memory use and CPU use.

Even if you can't open it, you can customize the applet to show memory use and CPU.

Another way is to have a terminal open and monitor things that are going on. You can also use the top command to look at running processes.

Regards,
Roger :cool:

---

### Post by tangibleorange on 2008-03-29
As suggested above, what i would do is to open a terminal when you first login and enter this command into it:
```
top
```

Then, when the computer starts to freeze up, try and change to the terminal window which has that command running inside it. It should tell you the process which is hogging all the memory and causing your computer to do that... (it will be the one at the top of the list)

---

### Post by Jaems on 2008-03-29
Thanks for the reply guys-

The culprit is _wrapndis_wg/1_. 

Is there any way around this? I can browse fine (until i choose to download something) and last time i checked synaptic doesnt cause it to happen (i'll check after i post this to make sure, not terribly interested in having to press the killswitch again.)

My wireless card driver should be the latest onboard series from ralink- sorry i cant remember the model number. Like i said i got the windows drivers from the system 32 folder in the vista install.

I'm going to see if it complains over LAN, but if anyone has any ideas...?

---

### Post by tangibleorange on 2008-03-29
so it is the wireless driver...

it would be quite helpful if you could remember the model number or chipset of the card you're using the ndiswrapper driver for. If it's an onboard card, try typing this at a terminal:

```
lspci
```

which should give you some clue as to the chipset of the card... when we know what driver to use we can move on from there... i know that i simply couldn't get my ralink rt61 to work with vista drivers, but when i found some xp ones, it worked fine.

---

### Post by Jaems on 2008-03-29
The problem is that lspci reads 'ralink unknown device'. The manual says nothing about what specific hardware it is, but i am fairly certain it is an RT2860
i found [http://scraping.icebo.org/index.php/2008/02/29/kubuntu-on-medion-akoya-md-96630/]("http://scraping.icebo.org/index.php/2008/02/29/kubuntu-on-medion-akoya-md-96630/")

This seems the same as mine save the HDD capaciy. Unfortunately i have NO IDEA what to make of all that, the way it's explained doesnt make much sense to me.....

Also, checking what drivers ndiswrapper can handle, i couldnt find it in the list- I may have overlooked something though. :S

---

### Post by tangibleorange on 2008-03-29
OK I have no experience with the RT2860, but have you tried using the native drivers provided by RaLink? They can be found [here.]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

It's worth trying to compile and install those (unless you have already of course). If you need some help compiling the driver from the source just ask :)

---

### Post by Jaems on 2008-03-29
ok...

I went to the site, got the bz2 file. I would love some help with this and will see how far i get.

But then i realised that i had brought the open with/save to disk dialogue up and it didnt crash..... [edit] tested this and it still crashes :S

Not sure if i am changing 
TARGET=LINUX
MODE=STA
in all of the instances it is in the file or just the fist one.

"& point the LINUX_SRC setting to the root of your linux header files (/usr/src/linux-headers-&#8230;)"
dont know where that is exactly....

---

### Post by tangibleorange on 2008-03-29
what file are you editing? you should just have to unzip the folder you download, 'cd' into it, and type:

```
sudo rmmod ndiswrapper
``` (to get rid of ndiswrapper, might not be necessary)
```
sudo make
```
```
sudo make install
```
```
sudo modprobe rt2860
```

to load the module. this will then disappear on a reboot, but we can sort that later if the above works...

---

### Post by Jaems on 2008-03-29
failed. Wouldn't compile. ndiswrapper doesnt work any more either.

---

### Post by tangibleorange on 2008-03-30
> **Jaems said:**
> failed. Wouldn't compile. ndiswrapper doesnt work any more either.

What compiler error does it give?

---

