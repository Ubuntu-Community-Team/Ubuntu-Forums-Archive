---
title: "Where is gnome?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by AilK on 2008-01-29
I am a complete novice. I bought ubuntu on CD for my son from a registered vendor and he tried to run it. Having read the installation guide online it all looked straightforward, however, he is left with no interface and is mighty frustrated. When we boot up from the CD, it sort of stops with the message
'running local boot scripts (/etc/rc.local)       [OK]
What can I do?

---

### Post by PmDematagoda on 2008-01-29
You usually get such a problem when the X-Server is improperly setup. If you could post the specifications of the PC then we can help you solve the problem.

---

### Post by chronic on 2008-01-29
PmDematagoda is probably right 

which version of ubuntu are you using?

what computer do you have?

if you want to try linux but the Live CD doesnt work then download the alternate CD and install it in a virtual machine. If you need help doing this then you just have to ask :guitar:

---

### Post by AilK on 2008-01-29
The computer is Acer AMD Athlon 64 dual core.
The version of ubuntu is 7.10

---

### Post by PmDematagoda on 2008-01-29
I am sorry AilK, but the brand and processor type alone will not help us much, could you please post the VGA card that is being used by the PC.

---

### Post by sdowney717 on 2008-01-29
perhaps this thread will help.

[https://answers.launchpad.net/ubuntu/+question/2812](https://answers.launchpad.net/ubuntu/+question/2812)
AMD64 problems

I got the same sort of problem trying Ubuntu 7.04 on an ACER 5050-4697
Althoug I quit the ubuntu installation, I went on with Debian etch (which is in
the base of Ubuntu, I understand).
For the time being, just disable acpi, acpi=ht or acpi=off in boot line, and be prepared to
further problems in case you have to "power up" devices such as Wifi.

My log of the installation process (still fighting) is at
[http://www.df.uba.ar/~solari/acer.html](http://www.df.uba.ar/~solari/acer.html)

I hope it helps
                      Hernan

---

### Post by igknighted on 2008-01-29
> **sdowney717 said:**
> perhaps this thread will help.

[https://answers.launchpad.net/ubuntu/+question/2812](https://answers.launchpad.net/ubuntu/+question/2812)
AMD64 problems

I got the same sort of problem trying Ubuntu 7.04 on an ACER 5050-4697
Althoug I quit the ubuntu installation, I went on with Debian etch (which is in
the base of Ubuntu, I understand).
For the time being, just disable acpi, acpi=ht or acpi=off in boot line, and be prepared to
further problems in case you have to "power up" devices such as Wifi.

My log of the installation process (still fighting) is at
[http://www.df.uba.ar/~solari/acer.html](http://www.df.uba.ar/~solari/acer.html)

I hope it helps
                      Hernan

What good is a laptop when booted with acpi=off?  You can't even track the battery status...

I have an acer laptop with that processor (Aspire 4250) and it gets a similar error... simply hit <ctrl>+<alt>+<f1> to get to a terminal, then run the command "sudo dpkg-reconfigure xserver-xorg".  Choose "vesa" from the list of video drivers, select your desired screen resolution (same as you use in windows usually) later, and select the default for everything else.  When it is done type the command "startx" and gnome should load.  Go ahead and do the install, it should remember your settings on reboot to the installed system.  Then use the restricted-manager to install the proper video drivers for your card (needs internet connection).  Hope this helps.

---

### Post by AilK on 2008-01-29
Many thanks igknighted; I followed your instructions and now have gnome. Have left son happily installing! Thanks to all who read and offered help; I'm sure we'll be back for more!

---

