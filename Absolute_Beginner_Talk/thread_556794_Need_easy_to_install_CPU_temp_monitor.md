---
title: "Need easy to install CPU temp monitor"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by CHSIsupplier on 2007-09-21
Please be kind! I know that this topic has been discussed on these forums. I've read through several of the threads, and I just don't get it. I've been using Linux (Ubuntu 7.04) for all of about 22 hours now, and I'm having a rough time catching on. I put together a machine to dedicate to Folding@Home, and I wanted to save money on the OS.

I have a Core 2 processor on a G965 Intel motherboard. Both cores of my processor are at a constant 100% usage...so I'd like to be able to monitor the temps. I've done "sudo apt-get" a hundred times so far (lm-sensors and the like) but I don't what to do from there. :confused:
Can someone please take pity on a complete noob and recommend a simple utility that I can install. I would love it if there was a utility that had "copy and paste" install instructions.

Thanks for your time

Jeff

---

### Post by RomeReactor on 2007-09-21
Hi. Sorry to suggest you use the terminal again, but I think this is what you're looking for:
```
sudo aptitude install sensors-applet
```
once it's installed, right-click on an empty space in your top panel (or bottom panel if you prefer), select **Add To Panel**, and look for **Hardware Sensors Monitor**.

---

### Post by Dr Small on 2007-09-21
Do not fret. If you forget, ask again. If you need help, just ask.

Now, when I want to use a sensor program, I usually use ksensors.
So, if you want to install it, run this command in the terminal:
```
sudo apt-get install ksensors
```

To run the program, once it is installed, type this:
```
ksensors
```

Now you can configure it, and set it up to watch your cpu temperature. :D

Dr Small

---

### Post by CHSIsupplier on 2007-09-21
Thank you both SO MUCH! I'm sure you all get tired of the noob questions, but I like the looks and options that Linux has to offer, and I want to stick with it. If it weren't for forums and users like yourselves, I would be stuck with buying another Windows license:mad:...not learning a new OS.

---

### Post by CHSIsupplier on 2007-09-21
UH OH. When I tried to put the applet on my task bar, it said "no sensors found"

After I installed ksensors, I typed "ksensors" into the terminal, I saw the app begin to start (a small graphic in the center of the screen), then the terminal said failed to start. 

Is there something else I need to have installed?

---

### Post by SoloSalsa on 2007-09-21
I think```
sudo sensors-detect
```, if not then 'sensors detect' with a space instead of a hyphen.  Run that, and just say 'yes' to everything.  It will check for all internal thermometers it can find.  In the end, it will ask if you want it added automatically: I just say yes, let everything go automatically, and all is well.  Sign out/in, and next time you try checking sensors, it should work fine.

I know nearly nothing of anything myself!  This is probably the only thing I remember from the countless guides I've read.  Good luck with it.

---

### Post by CHSIsupplier on 2007-09-21
OK...that appeared to do something. now it says:

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
#----cut here----


What does this mean?


EDIT: ksensors is working now, but it doesn't give me an option for temps...only CPU speed, RAM usage, CPU state, and a couple of others.

---

### Post by RomeReactor on 2007-09-21
Now that the sensors are detected, try using the **Hardware Sensors Monitor** applet...

---

### Post by anemptygun on 2007-09-21
Thanks for the info guys, I'll take advantage of this too.

---

### Post by CHSIsupplier on 2007-09-21
The applet just says "no sensors found". 
This mobo does have temp sensors because I can look at the temps in the BIOS. There must be something else I'm missing. I appreciate all the help you guys are giving me!

---

### Post by SoloSalsa on 2007-09-23
I'm glad I could help.  The only thing I knew how to do was 'sensors-detect'.  I assume you said 'yes' and let it add the sensors data automatically.  Run sensors in a terminal (just that one-word command: sensors).  It should return all thermometer and tachometer values it can find.  If temperature is not listed there, then your hardware may be unsupported.

---

### Post by JBAlaska on 2007-09-23
Check out GKrellM ```
http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html
```

Use synaptic and serch for gkrellm

---

### Post by jeremy1138 on 2007-11-06
Hi I just installed conky on my computer and I'm having trouble getting the cpu temp to work.  I also installed the sensors applet and that doesnt show cpu temp either...  It just says 0 degrees C.  When I type in acpi -t, I get:
```

jeremy@jeremy-laptop:~$ acpi -t
     Battery 1: charged, 100%
     Thermal 1: ok, 0.0 degrees C

```
I also tried sensors-detect and no dice there either:
```

jeremy@jeremy-laptop:~$ sudo sensors-detect
[sudo] password for jeremy:
sudo: sensors-detect: command not found

```
Does anyone have any idea how I can get it working?  Thanks in advance for any help you can give!

---

### Post by jeremy1138 on 2007-11-07
Does anyone know what command may have replaced the sensors-detect command?  I'd like to at least find out if I even have a temp sensor...  My laptop must have a temperature sensor right?  Any ideas would be greatly appreciated.  Thanks!

---

### Post by cwgannon on 2007-11-07
The command for me (running Gutsy) is still "sudo sensors-detect" -- perhaps you were missing the 'sudo'?

---

### Post by jeremy1138 on 2007-11-08
Thanks for the response!  For some reason that command does not work for me.  I made sure to include sudo.  This is what I get when I try it:
```

jeremy@jeremy-laptop:~$ sudo sensors-detect
[sudo] password for jeremy:
sudo: sensors-detect: command not found

```
Is there another command that might tell me similar information?  Or does something need to be installed so I can execute this command?

---

### Post by jasexavier on 2008-05-20
I had the same problem with the "sensors" command.  You need to install the sensors libraries: ```
sudo apt-get install lm-sensors
```

After that the sensors-detect command should work fine.

---

