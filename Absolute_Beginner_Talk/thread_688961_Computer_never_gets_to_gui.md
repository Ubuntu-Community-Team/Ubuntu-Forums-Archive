---
title: "Computer never gets to gui"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by tjb_15 on 2008-02-05
After trying to install a sound card, I restarted my computer and now It takes me to a terminal.

---

### Post by spiderbatdad on 2008-02-05
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by emarkd on 2008-02-05
I think you're going to have to post a little more information.  What steps did you take to install your sound card?  What sort of hardware do you have?  Are there any messages given?

For something to try, run:

```
sudo /etc/init.d/gdm restart
```

but that's just a guess with no more information to go on.

---

### Post by tjb_15 on 2008-02-05
Neither Worked

Heres some commands I used to install my sound card

```

sudo apt-get install po-debconf
sudo apt-get install debhelper
sudo apt-get install quilt
sudo apt-get install libc6-dev
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure
make
sudo make install
alsamixer                        
cat /proc/asound/card0/codec#* | grep Codec                 #All was fine until some where after here
modprobe snd-ens1371
cat /proc/asound/card0/codec#* | grep Codec
cat /proc/asound/cards
lsmod | grep snd
sudo modprobe -r snd_ens1371
sudo modprobe snd_ens1371

```
This is the output of **lspci**
```
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 82)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 12)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 08)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
00:10.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:13.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
00:14.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Thanks for your replys
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by tjb_15 on 2008-02-06
I've Been looking on google and can't find a thing. Could Some one help me?

---

