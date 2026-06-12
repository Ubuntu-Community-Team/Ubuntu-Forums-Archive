---
title: "How do I determine what graphics card I have?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by hkim on 2007-04-17
How do I determine what graphics card I have?:confused:

---

### Post by bwhite82 on 2007-04-17
In a console type:

> lspci

---

### Post by zvacet on 2007-04-17
```
lshw
```

---

### Post by hkim on 2007-04-17
Cool, Thanks.

Here's what I found:

hkim@hkim-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chi pset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)Now what do I do to upgrade my graphics card so that I can run google earth more quickly?
Thanks for all of your help.
0000:01:0b.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Mode m (rev 08)
hkim@hkim-desktop:~$ lshw
WARNING: you should run this program as super-user.
hkim-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Celeron (CoppermIntel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)ine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0hkim@hkim-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chi pset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel CoIntel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)rporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)
0000:01:0b.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Mode m (rev 08)
hkim@hkim-desktop:~$ lshw
WARNING: you should run this program as super-user.
hkim-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 82810E DC-133 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810E DC-133 CGC [Chipset Graphics Controller]
             vendor: Intel Corporat
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 82810E DC-133 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810E DC-133 CGC [Chipset Graphics Controller]
             vendor: Intel Corporat

[COLOR="Red"][B]Now what do I do to upgrade my graphics card so that I can run google earth more quickly?
Thanks for all of your help.[/B][/COLOR]

---

### Post by Razorback on 2007-04-17
It looks like you have on-board graphics.  What type of computer are you using?  I had an old Compaq Deskpro with that chipset.  Depending on your motherboard layout, you could use an AGP card or PCI card.

---

### Post by hkim on 2007-04-17
This is an old Gateway Essential? I guess.:)

---

### Post by Razorback on 2007-04-17
Have you opened the case to see what expansion slots are on motherboard?

---

### Post by hkim on 2007-04-17
OK, I have the case open. I not really sure what I shout be looking for. There are two open slots toward the bottom and back of the machine.
Thanks for your patience as I'm pretty green when it comes to this stuff.

---

### Post by Razorback on 2007-04-17
Do you know what model of Gateway you are using?  Those are probably expansion slots where you could install a new graphics card.  Is there a removable tab behind the slots located on the case?

If you install a new card, usually you need to go into the bios when the pc is booting up and disable the onboard graphics after the card is installed.  If you can give the model, it should be pretty easy to figure out what you need to do.

---

### Post by hkim on 2007-04-17
I think the model is MICRO ATX BRY Essential 566C. And yes, there are removable tabs behind the slots. The other slots have the ethernet and dial up cards and connections.

---

### Post by Razorback on 2007-04-17
It looks like the pc comes with two expansion slots so you should be able to buy a PCI video card and use it as long as your bios allows you to disable the onboard graphics.

---

### Post by hkim on 2007-04-17
> **Razorback said:**
> It looks like the pc comes with two expansion slots so you should be able to buy a PCI video card and use it as long as your bios allows you to disable the onboard graphics.

Should I get the PCI VGA or TV-Out or NVIDIA PCI Express. Also, how do I disable the onboard graphics?   Thanks

---

### Post by Razorback on 2007-04-17
PCI VGA - Nvidia seems to work better with Linux.  You can probably get a used one on Ebay for ~$40.  If you have the manual that came with the PC you should be able to see if the onboard graphics can be disabled.  I believe the Compaq found the card automatically but I am not sure.  Otherwise, you have to access the bios while the pc is booting up.  Different bios developers use different keys to access the bios;  AMI uses the del key.  Once in the bios, you need to navigate through the screens to find where to disable it.

---

### Post by hkim on 2007-04-17
thanks for all of your help

---

### Post by Razorback on 2007-04-17
Well, I hope I haven't confused you too much. :)  It would be great if all PC manufacturers could get together and make a standard way of configuring!

---

### Post by hkim on 2007-04-17
Not at all,that was good advice. I installed the new video card and resent the BIOS to PCI. Now , Ubuntu goes thru it's system checks - everything ok - then the screen goes to black with a blinking cursor in the upper right hand corner and the freezes up. I spoke with the tech support for the new card and they suggested I pull the battery on the motherboard to reset the bios, but that didn't work. They also suggested I get a bios update. Does this sound correct and if so, where should I look for the update and how much should I expect to pay? Thanks

---

### Post by Razorback on 2007-04-17
You need to reconfigure X for the new video card.  I ran into the same thing when I changed video cards.  What type of card are you using: ati, nvidia,...

---

### Post by Razorback on 2007-04-17
Boot in recovery mode by hitting the esc key when grub loads (before ubuntu splash screen).

type:
 sudo dpkg-reconfigure xserver-xorg

Answer questions and make sure you select the correct video card.

---

### Post by hkim on 2007-04-18
I'm using the nvidia card. When I hit esc during grub mode. I get:

Ubuntu, kernel 2.6.15-28-386 (with and without) (recovery mode) twice
and the choice to type e to edit and c for a command line.
I typed c and the the text you recommended and got

grub> error 27: unrecognized command. 

what next?:D

---

### Post by Razorback on 2007-04-18
> **hkim said:**
> I'm using the nvidia card. When I hit esc during grub mode. I get:

Ubuntu, kernel 2.6.15-28-386 (with and without) (recovery mode) twice
and the choice to type e to edit and c for a command line.
I typed c and the the text you recommended and got

grub> error 27: unrecognized command. 

what next?:D

Highlight kernel 2.6.15-28-386 (recovery mode) and hit enter.  The machine will boot in recovery mode and stop at the command line (similar to DOS).
Then type:
sudo dpkg-reconfigure xserver-xorg

Answer questions and make sure you select the nv or nvidia (can't remember) driver.

---

