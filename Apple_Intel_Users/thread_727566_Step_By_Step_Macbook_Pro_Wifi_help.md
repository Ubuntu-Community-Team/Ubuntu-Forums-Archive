---
title: "Step By Step Macbook Pro Wifi help"
date: 2008-03-17
forum: Apple Intel Users
---

### Post by ThatGuyThere on 2008-03-17
I'm pretty new to ubuntu, and I need some help setting it up for my Macbook Pro (2.2 GHZ, Nvidia 8600), and i can't figure it out. I've tried a few other methods, but I can't get it to work :( I don't want to have to keep using ethernet!

---

### Post by mbp84 on 2008-03-17
Ok what I did was go off of this site but I had to change it a little.  The stuff that I bolded is what I changed and it worked like a charm.


[http://ubuntu-tutorials.com/2007/08/02/how-to-setup-wireless-on-a-macbook-using-madwifi-710-gutsy/](http://ubuntu-tutorials.com/2007/08/02/how-to-setup-wireless-on-a-macbook-using-madwifi-710-gutsy/)


    sudo aptitude install build-essential

    wget [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)**_madwifi-dfs-current.tar.gz_**

    tar -zxvf madwifi [tab]

    cd madwifi [tab]

    make

    sudo make install (answer 'r' when asked about previous modules)

---

### Post by cyberdork33 on 2008-03-18
I don't know why you would need the dfs branch, but whatever.... if it works, it works.

---

### Post by ThatGuyThere on 2008-03-18
I tried that solution, copy-pasted the text into konsole, and let it run. No errors showed, BUT it didn't work, before or after a restart.

---

### Post by cyberdork33 on 2008-03-18
You may need to block the Ubuntu driver to make sure you are using the compiled driver as is explained at the top of this page:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Also, you need to make sure you have a atheros card if you are trying to use madwifi, otherwise you can only use ndiswrapper (Broadcom cards).

What is the output of lspci?

---

### Post by ThatGuyThere on 2008-03-18
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)


That's the outcome of lspci.

---

### Post by mbp84 on 2008-03-18
> **cyberdork33 said:**
> I don't know why you would need the dfs branch, but whatever.... if it works, it works.

I have no idea.  Im new to linux.  First time using it for me and it seemed like the steps in the instruction page i went to had like a bad link so I changed it to that one did the commands and now i have wireless so I couldn't be happier.

---

### Post by ThatGuyThere on 2008-03-18
I also did a 
sudo apt-get install linux-restricted-modules-$(uname -r)
But it tells me that it's already installed.

---

### Post by cyberdork33 on 2008-03-18
> **ThatGuyThere said:**
> I also did a 
sudo apt-get install linux-restricted-modules-$(uname -r)
But it tells me that it's already installed.
but that is what I am saying... Since the restricted modules are installed, you need to block one of them (the atheros module) so that the one that you want loads instead.
> If you decide you absolutely need to compile madwifi from SVN, then you must **stop the linux-restricted-modules package from providing the madwifi module ath_hal, via its so called volatile module mechanism**. Do so by adding **ath_hal** to the list of **DISABLED_MODULES** in **/etc/default/linux-restricted-modules-common**.

---

### Post by ThatGuyThere on 2008-03-18
It won't let me save it :( When I was installing the OS, it never asked me for any root passwords or anything. How do I get it to save?

---

### Post by cyberdork33 on 2008-03-18
> **ThatGuyThere said:**
> It won't let me save it :( When I was installing the OS, it never asked me for any root passwords or anything. How do I get it to save?
The root password is randomized by default because you should NEVER need to login as root.

To temporarily get a root prompt, use 'su'.

Normally though, to make normal config file edits and such, you just need root privs for one command, so we can use the 'sudo' command in front of the normal command you want to run. For instance, if I were to, say, try to edit /etc/default/linux-restricted-modules-common with gedit (the default text editor), I might use the following command:
```
sudo gedit /etc/default/linux-restricted-modules-common
```A similar syntax should be used to edit almost any file outside your home directory.

---

### Post by ThatGuyThere on 2008-03-19
It doesn't open anything for me. My sound recently also disabled itself, and it isn't going back up (after working fine for a while). EDIT: Neither does the package manager, or anything else for that matter. I think I have to reinstall Ubuntu, and this'll be the second time :/

---

