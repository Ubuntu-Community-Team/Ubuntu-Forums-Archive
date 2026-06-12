---
title: "ATHEROS wireless not appearing in iwconfig and ifconfig but appears with lspci"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by baterista on 2008-02-27
So... after looking for an answer for an hour around the internets, I give up.
I'm happy though, I got 7.10+compiz to work on my ati card :)

So here's the deal: I have a lenovo t60 with an Atheros abgn card. It shows up with lspci as:> 
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

And yet output for ifconfig is following:
> eth0      Link encap:Ethernet  HWaddr 00:16:41:E2:11:40  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fee2:1140/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9612109 (9.1 MB)  TX bytes:825299 (805.9 KB)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)

Also, iwconfig shows the following:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

 
I've been able to install madwifi without a hitch, but there's no point of running the driver with the hardware not recognized... Help!

Thanks in advance,
baterista

---

### Post by igknighted on 2008-02-27
Ewww... don't go anywhere near iwconfig.  I say this in jest, but the point remains.  NetworkManager should handle all the configuration for that card, just click the unplugged network cable icon in the system tray and select your wireless network from there.  Fiddling with iwconfig and the like can actually keep NetworkManager from working.

EDIT: did you check the madwifi page to see if that card is supported yet?  N wireless is more miss than hit right now on linux.

EDIT #2: You should have an ath0 shown.  Did you run the restricted driver manager?  I used a laptop with an Atheros chip and it always worked right out of the box, or was a couple clicks away with the restricted manager

---

### Post by jonnywombat on 2008-02-27
I got my Atheros wifi working by following the instructions in this thread....[http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874](http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874)

Using Ndiswrapper

However I had all sorts of problems using ubuntu 64bit which I never resolved, but switching to 32bit made it all a breeze.

Hope that helps

Jonny

---

### Post by baterista on 2008-02-27
Yeah, that's the first thing i looked at. The only options are Wired Network and Manual config. When i click on manual config, only the wired connection and a disabled telephone modem connection are there.

---

### Post by jeffus_il on 2008-02-27
What does the output of ```
dmesg
``` in a terminal say about your card. You could try ```
dmesg | grep ath
``` to save you some searching. After checking that out, Which module is the correct one for your card? I think it will be ath_pci.
So check to see if it is loaded using```
 lsmod | grep ath
```, if not do a```
 sudo modprobe ath_pci 
```and the look at the end of dmesg to see the output. If the module is loading you have to consider using a later version of madwifi than the one supplied in the restricted drivers package supplied by Ubuntu. You should not have to do this.

---

### Post by baterista on 2008-02-27
UPDATE:
I also checked  lshw -C network and this shows the wireless network as UNCLAIMED... wtf?
\\
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
\\

Does that help?

---

### Post by baterista on 2008-02-27
Jeffus, in response to your inquiries, here's what i got from dmesg | grep ath

[ 1994.910146] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1994.928327] ath_pci: 0.9.4

for lsmod | grep ath the following:

ath_pci               107568  0 
wlan                  225312  1 ath_pci
ath_hal               219888  1 ath_pci


and for  sudo modprobe ath_pci -> dmesg

[ 1994.928327] ath_pci: 0.9.4

So it seems something is there, yet idk why it doesnt register...

---

### Post by jeffus_il on 2008-02-27
Yes, the driver module is there. Here is someone who had the same problem as yours but on Mepis. which shouldn't make a difference. Look at this page, it seems that you may have to build the latest driver from source.
 [http://www.mepislovers.org/forums/showthread.php?p=105887](http://www.mepislovers.org/forums/showthread.php?p=105887)

---

### Post by baterista on 2008-02-27
Hmm followed the instructions in that link, but no go. Still not recognized by iwconfig after the modprobe...

---

### Post by jeffus_il on 2008-02-27
A shot in the dark:
I have a machine that I needed to pass the parameter ```
pci=noacpi
``` to the grub kernel line in order for the card to be recognized, Want to try it?

---

### Post by baterista on 2008-02-27
So how would i got about doing that?

---

### Post by jeffus_il on 2008-02-27
You could test it first by 
[LIST]
[*]rebooting
[*]Hitting <esc> at the grub menu
[*]Hitting "e" for edit
[*]highlighting the line starting with kernel
[*]I think an "e" again
[*]go to end of kernel line
[*]add "pci=noacpi"
[*]hit "b" to boot[/LIST]
If this works edit the change into the file /boot/grub/menu.lst afterwards.

---

### Post by baterista on 2008-02-27
awesome! we got somewhere. now iwconfig recognizes ath0
also, device manager recognizes the card! 
all thats left is to connect
i'll let you know how it goes.

also, can you explain what that sequence to the kernel does?

---

### Post by baterista on 2008-02-27
Dude... mark this one as SOLVED! Thanks so much. But please explain the shot in the dark. What does it do? Just curious.

---

### Post by jeffus_il on 2008-02-27
I'm not an expert on this, each pci card has an interrupt address, you can either leave it as it is or let the acpi system handle allocating the interrupt. In this case there seems to be some problem due to hardware changes in the card and/or driver changes, so that the system was not picking up the correct interrupt for your card and therefore not seeing it. Getting rid of the acpi pci handler left it as it was and let the driver see it, if you google a bit you may find a better explanation!

---

