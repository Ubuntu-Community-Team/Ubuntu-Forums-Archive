---
title: "help with video cards"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-05
how do i get ubuntu to use my pci graphics card over my onboard graphic card and i cant disable it from the bios or jumper settings

---

### Post by dcstar on 2006-04-05
[QUOTE=slipk487]how do i get ubuntu to use my pci graphics card over my onboard graphic card and i cant disable it from the bios or jumper settings[/QUOTE]
If it is actually detected (and working), change the X system to use it by:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by meborc on 2006-04-05
i have read that it is suggested to use

**sudo dpkg-reconfigure -phigh xserver-xorg**
instead of
**sudo dpkg-reconfigure xserver-xorg**

just a thought ;)

---

### Post by az on 2006-04-05
[QUOTE=meborc]i have read that it is suggested to use

**sudo dpkg-reconfigure -phigh xserver-xorg**
instead of
**sudo dpkg-reconfigure xserver-xorg**
[/QUOTE]

You need to run it without the -phigh switch for it to ask you the questions.  You need to tell it to use the non-default card.  The -phigh switch will just cause it to take the default and ignore your second card.

Usually, your motherboard handles this in the bios, and not by jumpers.  Most bioses default to using the second card as opposed to the onboard one if you chose to reset the bios to factory settings.  The option is sometimes a chioce between using the agp or pci video adapter.  What video adapter options do you get in your bios?

---

### Post by meborc on 2006-04-05
[QUOTE=azz]You need to run it without the -phigh switch for it to ask you the questions.  You need to tell it to use the non-default card.  The -phigh switch will just cause it to take the default and ignore your second card.

Usually, your motherboard handles this in the bios, and not by jumpers.  Most bioses default to using the second card as opposed to the onboard one if you chose to reset the bios to factory settings.  The option is sometimes a chioce between using the agp or pci video adapter.  What video adapter options do you get in your bios?[/QUOTE]

thanks azz for clarifying... :D never knew that

---

### Post by slipk487 on 2006-04-05
ih cant get a graphical boot when i have the pci card in and last time i used

```
sudo dpkg-reconfigure xserver-xorg
```

it gave me no option to slect my pci card but i try again

---

### Post by az on 2006-04-05
[QUOTE=slipk487]ih cant get a graphical boot when i have the pci card in and last time i used

```
sudo dpkg-reconfigure xserver-xorg
```

it gave me no option to slect my pci card but i try again[/QUOTE]
It may be that your card is not working properly, or not working with your botherboard.

---

### Post by nin881 on 2006-04-05
If it's anything like debian, which i believe it is, It will ask for the location of the card. you will have to do a lspci to find the location. Correct me if I'm wrong. I've never had to do this in Ubuntu.

---

### Post by slipk487 on 2006-04-05
what driver do i scelect for a Radeon 9250 because i used the one that said ATI and i didnt work

---

### Post by Jason_25 on 2006-04-05
Put the hardware address of the card you want to use in the device section of the xorg file.  Be sure to use the same format as the file uses.  For example, mine looks like 
```

BusID           "PCI:5:0:0"

```

---

### Post by slipk487 on 2006-04-05
will this work  

You do not need to take all these steps if you run an up-to-date Breezy installation on a 32 bit system. Dennis Kaarsemaker provides these packages in a repository. Add the following line to /etc/apt/sources.list: 

deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) breezy-seveas drivers

Then you can simply install the ubuntu-fglrx-$arch (see above for the meaning of $arch) package

---

### Post by slipk487 on 2006-04-05
how do i figure out the pci bus id because i found out that that is the problem with the x server afer setting up my card

---

### Post by az on 2006-04-05
Type 

lspci 

and post the output.

---

### Post by slipk487 on 2006-04-05
there but i dont have the Radeon Card in because i cant get to the logon if its not set up

```
0000:00:00.0 Host bridge: Intel Corp. 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)

```

---

### Post by az on 2006-04-05
0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)

That card's pci id would be 00.01.00.

You can do lspci from the command line.

But if you have to boot with your new card taken out, I presume it's because you have to switch the video adapter plug to the new card to see the bios display and so forth.  That would mean it is the default card and so you wouldn't have to change anything.  The xserver will detect and reconfigure X for that card by default if you run dpkg-reconfigure xserver-xorg.

That is not exactly what you asked originaly.

---

### Post by slipk487 on 2006-04-05
ill run lspci from Recovery concle and trie and figure it out and post what happens

---

### Post by slipk487 on 2006-04-05
thanks for the help i got it to work and ive been trying for a week now my id was 01:08:00 and now im going to find out if my tv out works

---

### Post by slipk487 on 2006-04-05
i cant use my tv out because my moniter gets to bright and the tv flickers but i dont really need it

---

