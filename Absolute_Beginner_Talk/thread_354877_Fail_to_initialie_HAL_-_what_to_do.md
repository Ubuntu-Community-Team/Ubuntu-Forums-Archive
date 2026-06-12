---
title: "Fail to initialie HAL - what to do?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Steffen.phx on 2007-02-06
Fail to initialize HAL! This failure window appears at ever start, shortly before my desktop is loaded. I can click away this failure and use Ubuntu normal, but I can't access to the device manager :(

Does anyone know how I can fix this problem? I use a Asus Notebook and Ubuntu 6.10 desktop CD.

Greet, Steffen

---

### Post by r4ik on 2007-02-06
try,
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

Good luck !

---

### Post by Average Joe on 2007-02-06
I have had the same problem a while ago. I "fixed" it by delaying my auto-login with 5 seconds. Then the HAL error message disappeared. My guess is that error occurs because some processes are not finished before others are started.

Anyway, you can delay your auto-login in System -> Administration -> Login Window -> Security -> Enable Timed Login.

I noticed after a while (some updates?) that I didn't have to use the delay option anymore. Now I am HAL-error free without using it.

Hope this helps.

---

### Post by marx2k on 2007-02-06
I had this exact error last night.  After 3 reboots, it is gone.

It seemed as though my sound blaster Audigy 2 also didnt work after that... I had to re-do the modprobe module installation thing... not sure if it totally fixed it... will find out on next reboot... but right now everything seems to be working OK with no problems and no HAL message on my last boot.

---

### Post by Steffen.phx on 2007-02-06
"sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12"

Must I have a running Internet connection or to insert the Ubuntu CD, because I tried this already, now I have the problem, that I need nearly ten minutes to start Ubuntu and the failure still appeares shortly before the Desktop is loaded.

But thanks for your quick answer, but this seems not to be working on my system :(

Greet, Steffen

---

### Post by r4ik on 2007-02-06
An internet connection would be nice :)

---

### Post by FLPCGuy on 2007-02-06
> **r4ik said:**
> try,
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

Good luck !
What exactly does this do (in plain English)?   I only get the "failed to initialize HAL" message infrequently but never figured out what it meant.  To me HAL means the hardware abstraction layer that translates between the specific CPU instruction set and the OS low level instructions.  If that didn't initialize the OS wouldn't run at all.  So it must mean something else in this error message.

---

### Post by r4ik on 2007-02-06
As far as i know it is  the USB Hotplug.
The command is supposed to "reset" but i must admid there are more HAL related failures such as graphics but those are followed by a error massage
as far as my knowledge goes.
In the worst case if HAL is to far "gone" is to reinstall.
But perhaps others can give some additional information so this HAL
problem can be solved once and for all.

---

### Post by FLPCGuy on 2007-02-06
> **r4ik said:**
> try,
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

Good luck !
Does anyone have a reference they can point me to for this command and it's parameters?  MAN doesn't show it.

---

### Post by r4ik on 2007-02-06
[http://www.ubuntuforums.org/showthread.php?t=331824&highlight=Fail+to+initialize+HAL](http://www.ubuntuforums.org/showthread.php?t=331824&highlight=Fail+to+initialize+HAL)
Post 7# and 8#

and,

[http://www.ubuntuforums.org/showthread.php?t=316907](http://www.ubuntuforums.org/showthread.php?t=316907)

[https://launchpad.net/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/ubuntu/+source/dbus/+bug/19577)

---

### Post by FLPCGuy on 2007-02-06
> **r4ik said:**
> [http://www.ubuntuforums.org/showthread.php?t=331824&highlight=Fail+to+initialize+HAL](http://www.ubuntuforums.org/showthread.php?t=331824&highlight=Fail+to+initialize+HAL)
Post 7# and 8#

and,

[http://www.ubuntuforums.org/showthread.php?t=316907](http://www.ubuntuforums.org/showthread.php?t=316907)

[https://launchpad.net/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/ubuntu/+source/dbus/+bug/19577)
Thanks for the references.  I'm still not sure why I'm getting this error intermittently.  I haven't been mounting anything USB.  I don't yet understand what dbus is or does. Also, I still don't have a clue what that command does so I'm hesitant to try it without knowing how to undo it.

I'm very happy with the way my system is working but don't feel confident enough in my manual backup or being able to restore my system to it's current configuration.

I have a lot to learn to be comfortable with my ability to run and repair my install of Ubuntu.

---

### Post by r4ik on 2007-02-06
Well i guess if it could be solved easy the prob would'nt be there anymore :)
Nothing wrong with a safe strategy.

Good luck !

---

### Post by MrHorus on 2007-02-07
I'm getting this too - started about a week ago.

I notice that the system hangs on boot at "Starting Hardware Abstraction Layer (HALd)" and won't progress after that.

If I boot an older (i386) kernel it boots (but HALd dies) and if I alter my K7 kernel entry in the boot menu to "acpi=off" it will boot but again, die in the background.

I know it dies as if I run dmesg it shows a Kernel Oops occuring along with a list of loaded modules and where the oops occured and yeah, it's HALd that brings the kernel down.

It's odd as I backed up home, etc and var onto my xbox and formatted the laptop to reinstall 6.06 but the fault is pretty much the same except it boots and gives the "HAL did not initialise" error.

Bit worrying that it's suddenly started doing this and persists after a clean install.

Hardware fault? :(

---

### Post by fuzzyturtle on 2007-02-07
i just fixed the same problem on my computer
by removing HAL completely and then reinstalling HAL and all the packages that depend on HAL (gnome-session and others) 
it know boots up without the error , but it still hasn't fixed the device manager 

i wouldn't suggest doing this until you have tried all other options

---

### Post by SouthernGorilla on 2007-03-12
I'm at the end of my rope here with this HAL issue.

I tried eliminating the auto login and adding a delayed login, didn't work.

I reinstalled everything through Synaptic, didn't work.

I tried this ```
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
``` didn't work

Every time I reboot it's the same story. I get the "Failed To Initialize HAL" error, my desktop background is missing, and Nautilus crashes. It says the CD/DVD creator in Nautilus is causing it to crash, but I'm not running it. I checked the fstab, neither of my DVD drives are automount. There is nothing connected to the USB ports except the receiver for the wireless mouse. It's been there since the first time I booted this computer and it still works just fine. I have to go into a terminal, remove the "pid" file and manually start dbus just to be able to open Nautilus. I believe I've tried every solution on this forum with no luck. Like most others who've had this problem, this is a recent development. This is a newly built computer and fresh install of ubuntu 6.10, the only OS that's ever been installed here. It ran fine for the first 3-4 months.

---

### Post by r4ik on 2007-03-12
Here is something to read might be A answer,

[http://www.ubuntuforums.org/showthread.php?t=186497&highlight=Fail+to+initialize+HAL](http://www.ubuntuforums.org/showthread.php?t=186497&highlight=Fail+to+initialize+HAL)

---

### Post by SouthernGorilla on 2007-03-12
> **r4ik said:**
> Here is something to read might be A answer,

[http://www.ubuntuforums.org/showthread.php?t=186497&highlight=Fail+to+initialize+HAL](http://www.ubuntuforums.org/showthread.php?t=186497&highlight=Fail+to+initialize+HAL)
That didn't work either. Not exactly clear what he did to solve the problem, I removed the entire file (after copying it, of course) and still get the message.

I also tried again using Synaptic to reinstall HAL and Nautilus, still no luck.

---

### Post by SouthernGorilla on 2007-03-13
> **fuzzyturtle said:**
> i just fixed the same problem on my computer
by removing HAL completely and then reinstalling HAL and all the packages that depend on HAL (gnome-session and others) 
it know boots up without the error , but it still hasn't fixed the device manager 

i wouldn't suggest doing this until you have tried all other options
How did you remove HAL without removing the whole desktop? I've tried several times to reinstall HAL through Synaptic along with everything else related to the problem and have had zero success.

---

