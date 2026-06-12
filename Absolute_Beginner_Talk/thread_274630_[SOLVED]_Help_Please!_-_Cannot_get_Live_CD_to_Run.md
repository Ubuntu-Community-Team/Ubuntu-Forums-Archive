---
title: "[SOLVED] Help Please! - Cannot get Live CD to Run"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Greg Knight on 2006-10-10
Hi All,

I am running into the same problem as a number of users.  When I launch the live cd (Dapper), my system boots up until I hear the 'Welcome' sound, but I am presented with the 'Black Screen with a little white line (BSWALWL)'

I am running on:
[COLOR="blue"]Processor:[/COLOR]
AMD64 3500+

[COLOR="blue"]RAM:[/COLOR]
1Gb (2 x 512Mb) Generic RAM
(I know it's not really generic, but what are the chances that it's the RAM...)

[COLOR="blue"]Motherboard:[/COLOR]
[GIGABYTE GA-K8N Pro-SLI]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1883&ModelName=GA-K8N%20Pro-SLI")

[COLOR="blue"]Graphics Adaptors:[/COLOR]
2 x nVidia 128Mb GT6600's in SLI
[GIGABYTE GV-NX66T128VP]("http://www.gigabyte.com.tw/Products/VGA/Products_Overview.aspx?ProductID=1216")

[COLOR="blue"]Disk:[/COLOR]
[WD Caviar® SE  WD1600JS 160 GB, 300 MB/s, 8 MB Cache, 7200 RPM]("http://www.westerndigital.com/en/products/Products.asp?DriveID=137")

I have tried both the 32bit and 64bit version of Ubuntu and the 64bit version of Kubuntu - Checked, double checked, reburned just in case - I now have a lovely stack of coasters if anyone is interested ;).

I have booted in safe mode; I have used nv, vesa, and nVidia drivers.  I have reconfigured Xorg, both manually and automagically.

and I'm stuck...](*,) 

I had no problems running, and then installing on my older system.  I just want to run the live CD first on this system (you know just to check that it works and stuff :rolleyes:)

If anybody has any ideas can you please let me know.

I know i'm a newb, I just can't stand feeling like a n00b.

Cheers!
Greg

---

### Post by petri on 2006-10-10
That is too common problem :confused: and you do have nvidia so you shouldn't have this problem.

Have you tried **acpi=off** when boot (start)?

Have you tried Ctrl + Alt + F1 (F1 to F6 gives you terminal, F7 GUI)

Ctrl + Alt + Backspace restarts your X (GUI)

EDIT: Noticed now :rolleyes:  you have **two** SLI cards. That might be the problem.

---

### Post by Greg Knight on 2006-10-10
> **petri said:**
> That is too common problem :confused: and you do have nvidia so you shouldn't have this problem.

Have you tried **acpi=off** when boot (start)?

Have you tried Ctrl + Alt + F1 (F1 to F6 gives you terminal, F7 GUI)

Ctrl + Alt + Backspace restarts your X (GUI)

EDIT: Noticed now :rolleyes:  you have **two** SLI cards. That might be the problem.

Hi Petri,
Sorry I should have been a bit more descriptive with what I have tried...

I have tried booting with acpi=off.

I can Ctrl + Alt + F1(to F6) - get to the CLI as expected.

From the CLI I have tried:
```
sudo nano -w /etc/X11/xorg.conf
``` and then manually editing xorg.conf

```
sudo dpkg-reconfigure xserver-xorg
```
both leavig everything as default; as well as trying nv, and vesa; also tried manually setting hor. and vert refresh rates.
```
sudo /etc/init.d/gdm force-reload
```

I also tried:
```
sudo apt-get install nvidia-glx
```

Ctrl + Alt + Backspace seems to have no effect.

> EDIT: Noticed now :rolleyes:  you have **two** SLI cards. That might be the problem.  I have tried swapping my video cable from one card to the other... is that what you meant??

Cheers!
Greg

---

### Post by ske1fr on 2006-10-10
I suspect petri means you'd find it easier if you had just one graphics card installed.:)

---

