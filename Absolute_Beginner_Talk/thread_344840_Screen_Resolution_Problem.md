---
title: "Screen Resolution Problem"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Philber on 2007-01-23
Hi, I have just installed Ubuntu (latest) to my PCs HD (with help from forum users) and cannot find a way to increase the screen resolution from 600/800.

At that resolution everything looks comically large. The machine is an old P3 Compaq Deskpro and the video, as far as I know, is just 'standard' motherboard video.

I took off WinXP to put Ubuntu on and it displayed at 1024/768 without a hitch.

Any ideas anyone?

---

### Post by taurus on 2007-01-23
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
lspci
```
That would tell you exactly what video card you have in your machine.

---

### Post by Sbarton on 2007-01-23
I saw this  [http://www.ubuntuforums.org/showthread.php?p=789696](http://www.ubuntuforums.org/showthread.php?p=789696)
That is a similar thread.
regards

---

### Post by Philber on 2007-01-23
Your input is much appreciated - am going to look into further tomorrow

---

### Post by harley_frog on 2007-01-23
I had the same problem with my wife's (I guess it's now OUR) computer after I installed MEPIS, which also uses X.org.  Check out this thread [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973) and see if that helps.

---

### Post by alienexplorers on 2007-01-23
Just enter the modeline created on this page [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) into your xorg.conf file under the monitor section as shown below.  You can change the refresh to what ever your monitor handles.


(Example)

Section "Monitor"
	Identifier	"Delta DE-570 BA"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	60-85
	Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
	Modeline "1280x768_85.00"  118.53  1280 1368 1504 1728  768 769 772 807  -HSync +Vsync
	Modeline "1280x960_70.00"  120.84  1280 1368 1504 1728  960 961 964 999  -HSync +Vsync
	Modeline "1280x1024_65.00"  119.40  1280 1368 1504 1728  1024 1025 1028 1063  -HSync +Vsync
EndSection

---

### Post by Philber on 2007-01-25
OK, struggling with this. The xorg.conf is a text file, which I have opened in gedit. It is a read only though.

To be honest I'm not really confident to change it anyway, and don't know what settings the monitor supports to be honest other than 1024/768. In other words I don't know what refresh rate is right.

Thanks for your help to date, any more help appreciated

Philber

---

### Post by Philber on 2007-01-25
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
lspci
```
That would tell you exactly what video card you have in your machine.

philber@philbers-Ubuntu-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:0e.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:0f.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
philber@philbers-Ubuntu-PC:~$

---

### Post by Sbarton on 2007-01-27
Philber, I have seen this [https://launchpad.net/debian/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/debian/+source/xserver-xorg-video-mga/+bug/58721)
I am not sure it will help you but it seems to be the same graphics card.
Sorry I cannot help any further.
regards

---

### Post by jvc26 on 2007-01-27
To open the read only files (if only for future reference) you have to launch them with a 'gksudo' command. This is because you are not logged in as the admin (to safeguard your computer) Hence to launch the xorg.conf you would need to go for:
```

gksudo gedit /path/to/xorg.conf

```
For more info on gksudo and sudo go to:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
For more info on root/sudo go to:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Il

---

### Post by Philber on 2007-01-27
Ok, thanks for that. I don't fully understand by I will give it a try. Thanks. Philber.

---

### Post by Philber on 2007-01-27
I will try that when I get a chance, though I'm nervous about editing that file. Thanks for your help. Philber

---

### Post by Xappe on 2007-01-27
why not try to reconfigure X:

```
sudo dpkg-reconfigure xserver-xorg
```
(this will get you to a text mode user inferface that'll guide you through the settings)

The default values should be ok, but when you come to the screen resolution and refresh rates part make sure to choose according to your system specs.

---

