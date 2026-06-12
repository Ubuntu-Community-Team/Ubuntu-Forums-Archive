---
title: "x server issue with new graphics card"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Blessed_Coffee on 2008-02-20
Hello there

I recently bought a new nvidia geforce 7600 to replace my fx 5500.  I now get a x server failure message on boot up.  Can anyone help me configure my x server, and install the proper drivers?  I have windows xp on a second IDE hard drive (ubuntu is on a sata hard drive :S), and I have linspire 5.0 on disc.  I don''t have an ubuntu disc at the moment, so I can't run unbuntu via live cd.  I am (or was) running ubuntu 7.10 gusty with GDE.

---

### Post by sisco311 on 2008-02-20
press Ctrl+ALt F1 to get tty sessoin and log in.
then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and start your x server:

```
startx
```

---

### Post by jan quark on 2008-02-20
try to boot into the recovery mode and run this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
startx
```

---

### Post by sisco311 on 2008-02-20
> **jan quark said:**
> try to boot into the recovery mode and run this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``````
startx
```

in recovery mode(single user mode) you don't need the sudo. you are automatically logged in as root.

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Blessed_Coffee on 2008-02-20
wow, thanks for the fast reply :D
everything seems to be running smoothly now :)

---

### Post by Blessed_Coffee on 2008-02-20
Hmm... not everything is running so smoothly.
Applications, such as games, are lagging pretty bad, even though they use to run fine with my 5500. :/

---

### Post by Blessed_Coffee on 2008-02-20
I've encountered something strange. My desktop is all messed up, and no opengl applications are loading anymore. :S

EDIT:  The shutdown and restart options are now gone, but standby and hibernate are still available.  When I boot up, ubuntu no longer takes me to the login screen.  I have to type startx, and it brings me to the desktop.

---

### Post by Blessed_Coffee on 2008-02-21
Should I just reinstall ubuntu? I've had this problem before with drivers, and I just reinstalled ubuntu, but that doesn't really solve the issue.  I still can't properly apply drivers in linux, and I'm not going to learn how to by reinstalling.

---

### Post by sisco311 on 2008-02-21
try to reinstall the drivers. go to the Restricted Drivers Manager  disable the driver(this will uninstall it) and enable the driver (this will install it)

or from the command line
```
sudo aptitude purge nvidia-glx-new
sudo aptitude install nvidia-glx-new
```

---

### Post by Blessed_Coffee on 2008-02-21
When I install the restricted drivers, it causes my x server to not load on the next boot.  It says that it found screen(s), but none are configured properly.

---

### Post by sisco311 on 2008-02-21
please post your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by Blessed_Coffee on 2008-02-22
This is without the restricted drivers.

---

### Post by sisco311 on 2008-02-22
and:
```
lspci
```

---

### Post by Blessed_Coffee on 2008-02-22
lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)

```

I attached my xorg.conf file after restricted drivers were installed.  Don't know if that will help.

---

### Post by sisco311 on 2008-02-22
you can try envy  to remove the drivers and install the proper one.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

sorry, i have no other ideas.

---

### Post by Blessed_Coffee on 2008-02-22
Okay, I'll try envy.  If envy doesn't work, then I'll just have to reinstall ubuntu.  Thanks for all your help :)

---

### Post by Blessed_Coffee on 2008-02-22
That did it!
Everything is running splendidly now.
  :D

---

