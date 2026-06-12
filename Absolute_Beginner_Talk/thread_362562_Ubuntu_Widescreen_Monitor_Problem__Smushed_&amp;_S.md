---
title: "Ubuntu Widescreen Monitor Problem / Smushed &amp; Stretched Text"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by dtg on 2007-02-15
when i take screen shots, you can't tell there's anything wrong, but in real life, staring at the monitor, the text's height gets stretched and squished down sometimes.

so i made an example in gimp

[img]http://i18.tinypic.com/48vvvk1.png[/img]

[size=4]**HALP!**[/size]

it does that stuff.

ps, i'm very sorry for my first post being a request for help, that's so not me =p

---

### Post by dtg on 2007-02-15
oh also, i have a semi-widescreen laptop monitor

it's 15 inches (like my penis) and about 10% wider than most 15 inch monitors (like my penis)

my internet penis anyway

thanks in advance

---

### Post by dtg on 2007-02-15
ps i'm on an everex stepnote

ghetto $490 walmart laptop

it's new though

new like my entire linux experience

it's enjoyable experience aside from this squishy text dilemma

if anybody helps me i'll snuggle with you all night long

---

### Post by dtg on 2007-02-15
Anyone?

---

### Post by dtg on 2007-02-15
Eh?

---

### Post by LinuxMum on 2007-02-15
well i am sure you could have left out the penis comments, but I'll suggest something anyway.. 
have you made sure that you have installed the correct drivers for your video card? and if so maybe try downloading and installing them again..  i am not totally sure of the specs for that lappy... but i hope you get it working =\
worth a try at least..

---

### Post by dtg on 2007-02-16
Thanks for trying to help.

Here's my PC: [http://www.walmart.com/catalog/product.do?product_id=5412015](http://www.walmart.com/catalog/product.do?product_id=5412015)

---

### Post by Spr0k3t on 2007-02-16
To give us an idea of the specifications according to linux, open up a terminal and type this in:

```
lspci
```

Do a copy paste of your information surrounding the output with [ code][ /code] blocks.

---

### Post by dtg on 2007-02-16
```
root@ubuntu:~# lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:06.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)

```

---

### Post by Spr0k3t on 2007-02-16
Unknown device 3344...

You should update your PCIID information.

```
sudo apt-get update-pciid
```

Post back the information if it updates.

---

### Post by dtg on 2007-02-17
> **Spr0k3t said:**
> Unknown device 3344...

You should update your PCIID information.

```
sudo apt-get update-pciid
```

Post back the information if it updates.
Hmm... Problem

```
root@ubuntu:~# sudo apt-get update-pciid
E: Invalid operation update-pciid
root@ubuntu:~#

```

---

### Post by Spr0k3t on 2007-02-19
Well shoot, I know there's a command I used to update the pciid information on my system at home.  I'm sorry to say if that wasn't it, I'm not sure what command I used then.  I know it didn't involve a kernel update either, so it wasn't the update/upgrade command.  Anyone else want to chime in on this one?

---

### Post by lukem on 2007-03-01
I'm having a problem that looks very similar, but just iin the vertical lines of text almost missing.  This is with a Gforce FX5200 and a 19" acer wide screen.

---

### Post by tictacman on 2007-04-05
I know this is a long dead thread, but I just stumbled across it and for anyone else interested:

Its not **sudo apt-get update-pciid**

Its **sudo update-pciids**

---

