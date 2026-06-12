---
title: "no sound"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Wonslung on 2007-01-18
hello, i'm new to ubuntu and linux..i love it so far but i'm having an issue getting sound working..i have a dell 8300 with a realtek ac97 integrated sound card
any help would be appreciated
thanks

---

### Post by deadgobby on 2007-01-18
Please see bug report and how to debug it.
 I am sorry to bring this on a person who is new to Linux. But Linux is not all ways perfect. The forum will try to help you to get it working.
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820)
Gobby

---

### Post by ComplexNumber on 2007-01-18
> **deadgobby said:**
> Please see bug report and how to debug it.
 I am sorry to bring this on a person who is new to Linux. But Linux is not all ways perfect. The forum will try to help you to get it working.
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820)
Gobby
how do you know its a bug from the information given?




> **Wonslung said:**
> hello, i'm new to ubuntu and linux..i love it so far but i'm having an issue getting sound working..i have a dell 8300 with a realtek ac97 integrated sound card
any help would be appreciated
thanks
do you have the volume applet on your panel? if not, add it the panel by right clicking on the panel and selecting 'Add to panel'. then right click on the volume applet and seect 'open volume control'. do you have anything that is muted or turned right down?

---

### Post by Wonslung on 2007-01-18
i have the volume control on the panel and nothing is muted...

---

### Post by Wonslung on 2007-01-18
i don't know if this will help but the output to lspci is 
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by ComplexNumber on 2007-01-18
ol, using the volume applet again, does it say that you are using the correct sound card whjen you go to 'File' in the menu and select 'change device'?

---

### Post by Wonslung on 2007-01-18
it lists intel ic hf which is selected...

---

### Post by ComplexNumber on 2007-01-18
> **Wonslung said:**
> it lists intel ic hf which is selected...
bit isn't AC97 the one that you are wanting to use?

---

### Post by Wonslung on 2007-01-18
this is hillarios


there are 5 outputs on the back of my computer for sound
the one it was hooked into worked fine for windows but not in linux
now i changed it to another one, it works for both
so the problem is solved though i have no earthly idea why it would be like that

i've seen 100's of people with the same computer as mine with the same problem when i googled this trying to solve this problem and i hope this helps them, i've been pulling my hair out 2 days now trying to fix this and i'm normally really good at this but who would think to check something like this
i mean, it works when i start up windows but not in ubuntu, it must be the os...well in this case it was the output i was using...they are color coded
black, this is where it was plugged in, yellow, right beside the black, then under that, blue green red
it works in green, red is for the mic...weird huh

---

### Post by ComplexNumber on 2007-01-18
so it was because you were using the wrong port.

---

### Post by Wonslung on 2007-01-18
yeah, i feel stupid....i haven't run across a problem like that since i started using computers years ago...i guess often times the simplest solution is the best...but i still don't know why the port the speakers was hooked to worked under windows....

---

