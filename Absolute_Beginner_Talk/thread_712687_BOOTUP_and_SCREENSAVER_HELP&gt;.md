---
title: "BOOTUP and SCREENSAVER HELP&gt;"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Stef11 on 2008-03-02
Firstly I am using Xubuntu.
The first problem is:
Each time i boot the system up i get to the stage were i type in my user name and password, after doing this if i dont continually move the mouse the screen stays black instead of bringing up my desktop.
The second problem is i just cant seem to get the screensaver to activate. Ive set the time to 4mins before the screensaver should come on but nothing happens, i still have my destop in front of me,

Please help, im getting sick of continually rebooting the pc and moving the mouse to try and get this o/s to go to my desktop.
Please can anyone help
Regards
Stef11

---

### Post by dcstar on 2008-03-02
> **Stef11 said:**
> Firstly I am using Xubuntu.
The first problem is:
Each time i boot the system up i get to the stage were i type in my user name and password, after doing this if i dont continually move the mouse the screen stays black instead of bringing up my desktop.
The second problem is i just cant seem to get the screensaver to activate. Ive set the time to 4mins before the screensaver should come on but nothing happens, i still have my destop in front of me,

Please help, im getting sick of continually rebooting the pc and moving the mouse to try and get this o/s to go to my desktop.
Please can anyone help
Regards
Stef11

Both issues sound like video driver problems, what is you hardware?

---

### Post by jan quark on 2008-03-02
please post the outpit from 

```
lspci
```

```
sudo lshw -C display
```

---

### Post by Stef11 on 2008-03-02
Thanks for replying, here is the required info:
stefan@stefan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Stef11 on 2008-03-02
*-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

---

### Post by Stef11 on 2008-03-03
Also the system is a P4 1.7G with 640meg of ram with a 10gig HD'
Waiting in anticipation
Regards
Stef11

---

### Post by Stef11 on 2008-03-03
Do i need to update the graphics controller driver?
Any help appreciated.
Regards
Stef11

---

### Post by Stef11 on 2008-03-06
I hope someone can help, PLEASE>
Regards
Stef11

---

### Post by Stef11 on 2008-03-09
Is there any other information i need to provide to try and solve these problems.
Help?
since the 1980s I used the ti994/A, then went to DOS, then win3.11 and warpO/S . XP and vista are fine but i wanted to see what linux had to offer. Im not quite ready to give up just yet on Xubuntu.
I have had a look at another offspring of unix and that is max o/s X.
Quite nice.
regards

---

### Post by erginemr on 2008-03-09
I am sorry but your problem is very specific and I don't have a clue on what it may be.

However I will suggest you a few generic tips to try. Maybe it will help maybe it won't:

(1) Try to boot into the Xubuntu Live CD environment and check whether this bizarre problem exists there as well. If not, open a terminal and write down:
```
gedit /etc/X11/xorg.conf
```
Copy it to a removable drive such as a pen drive and post its contents here if the Live CD works normally.

(2) The same file controls your graphics settings in your installed system, too. SO, please post what is inside here:
```
gedit /etc/X11/xorg.conf
```

(3) You may try to let the system reconfigure it, in the hope that it might eliminate the problem. For that, first back up your current configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```
Then, run the config tool with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart your X server by changing to a virtual terminal (Ctrl+Alt+F1-6), logging in with your user name and password and issuing:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

If it does not work but you can login to the grphical system, post the contents of the resulting file here too. 

If worse comes to worst and you are stuck to the text screen,  you can restore your previous settings with:
```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```

No promises though, as yours is a very specific and rare problem. Good luck.

---

