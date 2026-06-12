---
title: "Xserver hell"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-08-19
i'm trying to configure my xorg file to use my ati 7000 (yes i know it's old) 

this is what i've tried so far

```
lshw -businfo
```

this showed that my card was in pci port 00:0b.0

when i do

```
sudo dpkg-reconfigure xserver-xorg
```

i get to the screen when i can type the full name of the card... i put in "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

then it takes me to the port

the default port is PCI:0:1:0

when i try typing in PCI:00:0b.0

it tells me that the format is wrong... even tho this is the correct number given to me by lshw 

ive tried every combination... what do i do?

---

### Post by taurus on 2007-08-19
Post

```
lspci | grep VGA
```

---

### Post by Tyke91 on 2007-08-19
one thing i've always wanted to know... how do you make that little

  | 

symbol. i usually copy paste, but these are different computers.

---

### Post by Tyke91 on 2007-08-19
wow... i didnt notice that button... on my keyboard it's 2 lines instead of one, but it makes the same symbol... thx. ill post that file shortly

---

### Post by Tyke91 on 2007-08-19
alright

output is 2 lines

00:01.0 VGA compatible controller - (the name of my intel card)

01:0b.0 VGA compatible controller - (the name of my ati card)

---

### Post by taurus on 2007-08-19
> **Tyke91 said:**
> alright

output is 2 lines

00:01.0 VGA compatible controller - (the name of my intel card)

**01:0b.0 VGA compatible controller** - (the name of my ati card)

If you want to use your add on graphic card, ATI, you need to go into your BIOS and turn off the onboard intel graphic controller.  

Reboot and see what's the output of that command this time with only one graphic card on your machine.

---

### Post by Tyke91 on 2007-08-19
i have no option to turn off the onboard controller... i already had the PCI card set to primary... what else can i do?

---

### Post by taurus on 2007-08-19
I suppose you don't have X running right now!  Do you have a copy of /etc/X11/xorg.conf on your machine?

Can you boot/run your machine with a LiveCD?

---

### Post by Tyke91 on 2007-08-19
the machine cannot run the live cd unfortunately :(

i have the xorg.conf file on my machine yes (actually, it's my moms computer... my computer runs ubuntu beautifully :D )

---

### Post by taurus on 2007-08-19
Can you post /etc/X11/xorg.conf?  Probably just have to replace the video BusID to the right one, ATI, in there.

```
cat /etc/X11/xorg.conf
```

---

### Post by Tyke91 on 2007-08-19
i can't post it, but i'll try editing it.

---

### Post by taurus on 2007-08-19
Remember, it's 0**1**:0b.0 and use vesa driver for your graphic card for now until you get X up and running.

---

### Post by Tyke91 on 2007-08-19
thx for being so helpful :)

one more question before i go off again... how do you edit text files without gedit? (in a command line interface)

---

### Post by Tyke91 on 2007-08-19
alright... i've edited that line to read

PCI:01:0b.0 

and i've set the driver to "ati"

it still doesnt work (it doesnt work with VGA either)

it keeps telling me that the ports arent in PCI:1:11:0

---

### Post by taurus on 2007-08-19
Gedit is for GUI.  For terminal, use nano.

```
sudo nano -Bw /etc/X11/xorg.conf
```
Move around with the arrows and when you want to save and exit, do <Ctrl>o and then <Ctrl>x.

---

### Post by taurus on 2007-08-19
> **Tyke91 said:**
> alright... i've edited that line to read

PCI:01:0b.0 

and i've set the driver to "ati"

it still doesnt work (it doesnt work with VGA either)

it keeps telling me that the ports arent in PCI:1:11:0

Can you at least post the sections that you've made the changes?

---

### Post by Tyke91 on 2007-08-19
kk... ill go write them down and retype them... brb

EDIT: alright

```
 Section "device"
     Identifier "ATI Technologies Radeon 7000"
     Driver "ati"
     BusID "PCI:01:0b.1"


```

---

### Post by eapache on 2007-08-19
Two things. In your previous post, you used 01:0b:0 not 01:0b:1. Secondly, the ati driver doesn't support cards before the 8000 (or so). Use 'radeon' instead (I have a 7200, which I too had to fudge to get working).

---

### Post by Tyke91 on 2007-08-19
sorry... that was a misquote... it really is 01:0b.0

that radeon thing didn't help at all

---

### Post by taurus on 2007-08-19
Try **vesa** driver for your graphic card.

---

### Post by eapache on 2007-08-20
In the section called 'screen' near the bottom, make sure that the device name is ATI Technologies Radeon 7000

---

### Post by h3hound on 2007-08-20
I had this same issue and converted the "0b" to decimal.  Thus, the entry is "PCI:1:11:0".

 That worked so successfully followed this: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)


good luck,
Ben

---

### Post by Tyke91 on 2007-08-21
WOW! it worked:guitar:

it never occured to me that it would be in hex

---

