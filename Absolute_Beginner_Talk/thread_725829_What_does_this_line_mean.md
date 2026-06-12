---
title: "What does this line mean?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by DarchAengel on 2008-03-16
I am trying to install Ubuntu in safe mode since it doesn't seem to work normally.  After all the indicators come up teling me what is happening this weird line came up.
> /etc/rc2.d/S20powernowd: 156 cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_govenor: Directory nonexistent
* CPU frequency scaling not supported

How do I address this probem?

---

### Post by gobbles414 on 2008-03-16
> **DarchAengel said:**
> I am trying to install Ubuntu in safe mode since it doesn't seem to work normally.  After all the indicators come up teling me what is happening this weird line came up.


How do I address this probem?

I don't know if installing from the LiveCD in safe mode is possible. You might need to use what's called the *Alternate CD* instead. You can download an Alternate CD from [here]("http://www.ubuntu.com/getubuntu/download"). Look for the checkbox directly below the *Start Download* button.

Does that help?

---

### Post by jordanmthomas on 2008-03-16
> **DarchAengel said:**
> 
How do I address this probem?

It could be that your processor doesn't support cpu scaling, as the message suggests.  What type of CPU do you have?
This shouldn't stop you from booting I don't think.  Does it still boot and you just don't like the message or does it hang up there?

---

### Post by DarchAengel on 2008-03-16
I have an Intel Celeron Processor.  It hangs soon after I get that message and the screen goes black.

---

### Post by Peter09 on 2008-03-16
What happens if you <CTRL><ALT><F1> at the black screen?

---

### Post by DarchAengel on 2008-03-16
Okay, I tried the alternate CD version.  It actually allowed me to install Ubuntu on the laptop.  But when I rebooted it gave me the same problem; it just hangs at a black screen.  I pressed Ctrl, Alt, F1 and this is what I got:

```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 7.10 ubuntu ttyl

ubuntu login:
```

What happened?

---

### Post by DarchAengel on 2008-03-16
I tried logging in at the prompt and it worked but there are still no graphics.  It just brings me to 

"user@ubuntu:`$"

---

### Post by handydan918 on 2008-03-16
Have you tried ```
sudo startx
```or```
sudo gdm
```

---

### Post by DarchAengel on 2008-03-16
Okay I tried both commands and this is what I got:

When I tried sudo startx:
```
xauth:  creating new authority file /home/deedlit/.serverauth.14552
xauth:  creating new authority file /home/deedlit/.Xauthority
xauth:  creating new authority file /home/deedlit/.Xauthority

X: Warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
             If this server is no longer running, remove /tmp/.X0-lock
             and start again.

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process 9errno 3):  Server error.
```

And this happened when I tried sudo gdm:

```
gdm[14573]: WARNING: GDM already running. Aborting!
GDM already running. Aborting!
```

---

### Post by gobbles414 on 2008-03-16
> **DarchAengel said:**
> I tried logging in at the prompt and it worked but there are still no graphics.  It just brings me to 

"user@ubuntu:`$"

I believe that your Dell Inspiron 1100 is rather old. Does it meet the system requirements for Ubuntu (click [here]("https://help.ubuntu.com/community/Installation/SystemRequirements/GutsyGibbon"))?

If your computer meets the minimum requirements, try this procedure:

1. Start your computer. Press the escape button on your keyboard as GRUB loads.
2. Choose the Rescue Mode for your highest kernel version. Allow Ubuntu to load.
3. Then type *sudo dpkg-reconfigure xserver-xorg* and press enter on your keyboard.
4. Follow the instructions in the wizard.
5. When you're done, type *sudo reboot* and then press enter.
6. Attempt to boot normally into Ubuntu.
7. Please let us know if this works. If not, please tell us which settings you chose in the wizard.

PS: I notice that you've asked another question on this topic [here]("http://ubuntuforums.org/showthread.php?t=725824"). In order for us to help you in the best/fastest manner possible, please post all related questions in a single thread.

---

### Post by DarchAengel on 2008-03-16
>  have made a live cd for Unbuntu, Kubuntu and even Xubuntu. None of them seem to be able to boot right on my Dell Inspirion 1100. It starts up easily enough but I never get out of the load screen and it seem to suddenly go to sleep. I can't tell. The cd drive slows and stops and the screen goes black without ever bringing up the desktop. Am I doing something wrong? Is there a way to install without having to use the live cd?

That is my post from the other thread.  In my haste to keep the problem up-to-date I failed to keep everything together.  I will post again once I tried your suggestions.

---

### Post by DarchAengel on 2008-03-16
kay, I checked my specs against the minimum requirements and everything seemed to check out.  I even tried to run the live xubuntu cd and am running into the same issues.

My progress so far:

I ran the previous commands and went through the install wizard.  I am still having the problem where the screen goes dark during boot and never comes out of it.  I'm evening noticing that it seems the backlight shuts down or at the very least dims a great deal.  This is the last thing I see before it freezes:

> * Checking Battery state...                                          [ OK ]
* Running local boot scripts (/etc/rc/.local)                              [ OK ]

At this point the screen flashes three or four times then goes dark.

As for my choices during xorg:

> Autodetect video hardware?    yes

x server driver?   intel

Identifier for video card:   Whatever they provided for me

video card's bus identifier:  I went with what they provided which was PCI:0:2:0

Amount of memory to be used by the video card:   left blank

Use kernel framebuffer device interface:   yes

Autodetect keyboard layout:   yes

Keyboard layout:   us

XKB rule set to use:   xorg

Keyboard model:   pc105

Keyboard variant:   left blank

Keyboard options:   left blank

mouse port:   /dev/input/mice  (Not sure what to pick for touchpad)

Mouse protocol:   ImPS/2

Emulate 3 button mouse:   no

Write default Files section to configuration file:   yes

Attempt monitor autodetection:   yes

Identifier for the monitor:   whatever they provided

Video modes to be used by the x server:   1024x768

Method for selecting the monitor characteristics:  Simple

Approximate monitor size:   17 inches (430mm)

Write monitor sync ranges to the configuration files:   yes

Desiered default color depth in bits:   24

I then come back to the prompt where I then reboot.  And then we come back to what I wrote above.  I know this computer is not that old and works just fine since I had Windows XP on there and it worked okay albeit a bit slow.

Does this make sense to anyone?

---

### Post by gobbles414 on 2008-03-17
Try choosing *VESA* instead of *Intel* for the *x server driver* option. In theory, one of two things will happen when you reboot. You could reboot straight into Ubuntu without any problems. Or, you could be presented with a warning that your screen resolution is low. If you get that warning, you'll have the option to attempt configuration of your screen again -- using a more friendly user interface than the command line one. According to my research, your laptop has the Intel 845GL chipset. So choose Intel 845 or as close as you can get, and then accept the changes.

Did this help?

---

### Post by DarchAengel on 2008-03-17
I thank and appreciate you sticking with me through this.  I tried what you suggested.  I had to do it twice since the first time went straight to a black screen.  I restarted and tried again and it went through but once I rebooted it came back to the same thing as before.

> * Starting anac(h)ronistic cron anacron   [ OK ]
* Starting deffered execution scheduler atd   [ OK ]
* Starting periodic command scheduler crond   [ OK ]
* Checking Battery state... [ OK ]
* Running local boot scripts (/etc/rc/.local) [ OK ] 

(That is the full extent of what has been on the screen.  It just took me a while to finally copy it down what with the flashing of the screen and then it blacking out)

What do you suggest next?

---

### Post by gobbles414 on 2008-03-18
> **DarchAengel said:**
> I thank and appreciate you sticking with me through this.  I tried what you suggested.  I had to do it twice since the first time went straight to a black screen.  I restarted and tried again and it went through but once I rebooted it came back to the same thing as before.

(That is the full extent of what has been on the screen.  It just took me a while to finally copy it down what with the flashing of the screen and then it blacking out)

What do you suggest next?

Thanks for posting the output. Everything looks normal. So check [here]("http://support.dell.com/support/downloads/") for an update to your computer's BIOS. If there's an update available, please install it and then try booting Ubuntu again. Also in your computer's BIOS, look for any graphics-related options that you can customize. And lastly in the BIOS, you might try disabling *legacy USB* support. Please let me know if any of this helps.

---

### Post by forrestcupp on 2008-03-18
Also, since you are using onboard graphics, you shouldn't leave it blank where it asks how much memory to dedicate to video.  I don't know how much RAM you have, but I would dedicate a minimum of 16 MB to onboard graphics.  If you have at least 256 MB of RAM, you might want to consider dedicating 32 or 64 MB.

And also, you're not trying to install the 64-bit version of Ubuntu, are you?  It won't work with your computer.

---

