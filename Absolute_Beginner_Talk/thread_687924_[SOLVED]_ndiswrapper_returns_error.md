---
title: "[SOLVED] ndiswrapper returns error"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ApatheticLoser on 2008-02-04
Hello, I am having problems getting my wireless network card to install with ndiswrapper.
The card is an Airlink AWLH6080, I'm using Ubuntu 7.10, I have the device CD, and the windows XP .inf file (NetAir101MIMO.inf)

I've tried running the graphical manager for ndiswrapper, and had it install the driver, but it returns the error Invalid driver. I'm unsure what to do at this point, or what information I can give to let you know more. 

Any help is greatly appreciated.

---

### Post by agim on 2008-02-04
I find its easier to use ndiswrapper from the command line. How are you connected to the internet right now? If you can download ndiswrapper from its website I can walk you through a command line install,

---

### Post by ApatheticLoser on 2008-02-04
I am, I'm using an ethernet print server thats acting like a hub, and connecting to my wireless setup.

---

### Post by ApatheticLoser on 2008-02-04
okay, I completely removed the ndiswrapper I had installed before, went to the site ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)) and downloaded ndiswrapper-1.52.tar.gz and I'm awaiting your instructions.

---

### Post by agim on 2008-02-04
okay. Here is my advice and my disclaimer. If it doesn't work, it will be easy to undo, but this is how I have used Ndiswrapper with about 20 installs. It has worked for me every time.

First, make a new directory to house your drivers. In a terminal type the following
mkdir wireless-drivers

this will make a directory called wireless-drivers. You can name it anything you want though.
Next, if you installed ndiswrapper from synaptic, uninstall it and download it from here:
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

From there here are the instructions I have followed with success. You will have to type each line into a terminal, except for the lines preceded with a #, these are just comments to help you along (if you already knew that I apologize).

#blacklist bcm43xx as you won't be using it.
sudo modprobe -r bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

#enable main repositories. If you don't know how to do this let me know.
sudo aptitude update
sudo aptitude install build-essential

uname -r
#after using this command you should get something like this : 2.6.24-14-generic. This will be referred to as <output> in the following paths.
sudo ln -s /usr/src/linux-headers-<output> /lib/modules/<output>/build

#switch to ndiswrapper directory
make distclean
make
sudo make install

#switch to wireless-driver directory
#place .inf (and maybe the .sys file, if you have it) into the wireless-driver directory
sudo ndiswrapper -i driver.inf
sudo modprobe ndiswrapper

#add word ndiswrapper to /etc/modules

there are more complicated instructions that I have seen, but this has worked for me.

---

### Post by agim on 2008-02-04
I had to edit the above, make sure you double check it by hitting refresh.

---

### Post by ApatheticLoser on 2008-02-04
> **agim said:**
> I had to edit the above, make sure you double check it by hitting refresh.

I caught it in between updates.. I've gotta check to see what was changed.. with what you had me do before, I think it installed, but I don't have the option of wireless settings with network config.

---

### Post by ApatheticLoser on 2008-02-04
The only change was to add "blacklist bcm43xx" to my /etc/modprobe.d/blacklist file, so I went ahead and did so, but I didn't notice a change.

---

### Post by agim on 2008-02-04
To see if it is working, type iwconfig in the terminal.

The only think I changed in the last update is the first command. Blacklisting the driver.

---

### Post by ApatheticLoser on 2008-02-04
apatheticloser@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by agim on 2008-02-04
Okay, you didn't get any errors when following the commands?

---

### Post by agim on 2008-02-04
If that doesn't work for you here is another method. but I would take a few minutes and repeat the steps from last time. Sorry about my editing!
[https://answers.launchpad.net/ubuntu/+question/19189](https://answers.launchpad.net/ubuntu/+question/19189)

It took me a long time to find something that worked for me (to use wireless) but when I did the switch was more than worth it. I hope you stick with it.

---

### Post by ApatheticLoser on 2008-02-04
So I guess my problem lies a step before ndiswrapper, I don't know if my system is seeing my network card, as a network card.

Is there a way to remove all the hardware listings for the pci 7:0:0 in ubuntu like there is in windows, so that I can install the hardware fresh?

---

### Post by agim on 2008-02-04
That's beyond me. To check your hardware, you can run this command

lscpi
or
lshw -C network

---

### Post by ApatheticLoser on 2008-02-04
I'll list the output from both of those, and maybe someone will know where to go from there. It might also be worth mentioning that this is a triple boot system (Vista, XP, Ubuntu) and running an 8800GT nvidia card. The wireless card works in the other boots, and it worked when I tried using it a few linux operating systems ago. (I've been tring a few, and Ubuntu seems the most friendly)

first: lshw -C network

  *-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:68:5d:0a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.6 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

Secondly lspci:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
07:00.0 Network controller: RaLink Unknown device 0601
07:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by ApatheticLoser on 2008-02-05
~Deleted~

---

### Post by ApatheticLoser on 2008-02-05
I'm still having problems with this, does anyone else have any possible solution?

---

### Post by Ptero-4 on 2008-02-05
You seems to have a Ralink chipset (IIRC it's nativelly supported under linux, if it isn't the driver you need is for a ralink, not the one you're trying to use).

---

### Post by Vadi on 2008-02-05
What does "sudo lshw -C network" give you?

---

### Post by ApatheticLoser on 2008-02-05
> **Ptero-4 said:**
> You seems to have a Ralink chipset (IIRC it's nativelly supported under linux, if it isn't the driver you need is for a ralink, not the one you're trying to use).

Would you please give me directions and a link to the correct driver then?

> **Vadi said:**
> What does "sudo lshw -C network" give you?

That was a sudo printout.

---

### Post by ApatheticLoser on 2008-02-05
I'm still completely lost if someone else has an idea?

---

### Post by Ptero-4 on 2008-02-07
The ralink driver I mentioned is supposed to be in the kernel already.

---

### Post by ApatheticLoser on 2008-02-07
Its not working for me though.

---

### Post by csmarkham on 2008-02-15
I had the same problem, and had both success and the same failure as Apathetic.

After trying the commercial Linuxant solution, my machine was wedged on boot. So 
I booted off the 7.10 CD.  I followed agim's instructions (thanks coming!) and it built
and installed. I got a good result from 'lshw -C network (matching Apathetic's listing
for the wireless device), and from  iwconfig, showing  my home router's SSID broadcast.

But of course I was modifying what was in memory from the CD boot. So I booted
into the recovery console, removed the Linuxant pkg and got back into a good boot
off my disk. 

I followed agim's instructions again, got a good build again, installed and ran
ndiswrapper against my NetAir101MIMO.inf file w/o error.  The devices appear
to be present in the /etc/ndiswrapper/

However, iwconfig shows "no wireless extensions". 

Since it worked off the CD boot, would something in the auto-config during install
have installed to block the use of ndiswrapper?

lspci still shows:  02:02.0 Network controller: RaLink Unknown device 0601
And lshw -C network now shows:
 *-network UNCLAIMED
          description: Network controller
          product: RaLink
          vendor: RaLink
         physical id: 2
          bus info: pci@0000:02:02.0
         version: 00
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list
         configuration: latency=64 maxlatency=4 mingnt=2

I should have preserved the output from the CD-ROM build and deployments; are those
going to be necessary clues for the differences?

Should I remove the PCI card, reinstall fresh, then put in the PCI card and re-install
ndiswrapper and the driver?  Or is there some other way to remove whatever is blocking
ndiswrapper?

It seems the initial install is what I have to undo to be able to get ndiswrapper to work again.
How could I do that?  Is there something else to put into the modprobe blacklist file, perhaps?

---

### Post by csmarkham on 2008-02-15
Uh, duh. A reboot got me closer.

Now my lshw shows in the configuration line that the ndiswrapper+netair101mimo is driver, 
and iwconfig shows what I saw before when I had the successful install from the CD boot.

Now I have to figure out how to configure wlan0, but that's for a different thread. :)

---

### Post by ApatheticLoser on 2008-02-16
I think you're right in thinking something with the boot-install blocked something, because I reformated, and was able to get it working using the rt2860.inf/sys driver intended for XP64bit. (dunno if it had to be this one, but for some reason I grabed it off the CD to try first.. and yes, I had tried this driver before the reformat.)

lspci still returns unknown Ralink device, but ndiswrapper lists hardware present, and actually setting up the wireless network to autoload at boot from the command line was pretty hassle free after learning the syntax words with the man page.

~The problem wasn't solved per say.. But its fixed, and no longer an issure, so I'll mark the thread solved. 
Thanks again for the responses and help everyone.

(on a side note, I feel like an expert with my 8800GT on ubuntu now, with how many times I've actually been able to get it installed. :-D )

---

### Post by Lee_is_alive on 2008-03-23
Hi,

In two of the threads I've found on rt2860 wireless driver, in the end it only worked after installing the driver for XP 64bit.. now my question, how do you get rt2860.sys and rt2864.inf out of the setup file? Is there a tool like winrar (this one can't do it though) that can open an setup.exe file and get these files out without actualy having to install this driver (wich I can't do as I don't run WIN XP 64bit)?

Thanks,

Lee

---

