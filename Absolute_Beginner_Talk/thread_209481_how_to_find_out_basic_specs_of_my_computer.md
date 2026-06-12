---
title: "how to find out basic specs of my computer"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-07-05
I need to find out the basic specs of my computer. You see, I posted a small notice in my community bulletin board and one person asked:

> What are the system specs? Ie CPU speed, disk size, ram size, video card, sound card, network card, etc? 

I already found out the cpu speed, disk size, and ram size,  but what info do i give for the Video Card, Sound Card, Network card?  And, in Ubuntu, how do i find out about the video card and sound card and network card?

My desktop pc has a ethernet modem. Is that what the  person wanted to know about network card? 

And what other basic info is he looking for when he writes "etc"?


I was advised to do  "lspci". I got the following info:
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
0000:01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)


Which line is about Sound Card? Which is about Video Card? And is Network Card "ethernet controller"?

---

### Post by taurus on 2006-07-05
You are not serious, right!  You don't know which line is your video, sound, or ethernet cards!!!
```

sound:
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)

video:
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)

ethernet:
0000:01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 7)

```
:roll:

---

### Post by richbarna on 2006-07-05
Go to System/Administration/Device Manager

EDIT: Ok so now you've edited and added the "lspci" command.

Yes, your network card is ethernet controller. 
It my be easier if you use the GUI Device Manager, it will give you more specific information that is easier to understan.

---

### Post by richbarna on 2006-07-05
[QUOTE=taurus]You are not serious, right!  You don't know which line is your video, sound, or ethernet cards!!!

:roll:[/QUOTE]

Nice reply, maybe you could have told him the command to get those results. Or do the rules say that if you are an Ubuntu Barrister you don't have to be polite  and helpful?

---

### Post by hanzj on 2006-07-05
Rich,
I think he just copied the text from my post number 1.


So my video card is "VGA Compatible Controller"? If I tell the people that, they might think it's just VGA, and not xVGA (where x is a letter). Please confirm. What kind of info should i tell them about video card?

When I did lpsci -vv, I got this info related to the VGA thingy:

0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 00be
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Region 1: Memory at ff000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

---------

So when someone asks for the specs of my video card, what is he looking for?

---

### Post by tommcd on 2006-07-05
Try "lshw" (without quotes) in terminal. The output is easier to read. On my system, for example,  the audio is:
*-multimedia
             description: Multimedia audio controller
             product: nForce3 250Gb AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:e800-e8ff ioport:e400-e47f iomemory:febfb000-febfbfff irq:193

ethernet is:
 *-bridge
             description: Ethernet interface
             product: CK8S Ethernet Controller
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@00:05.0
             logical name: eth0
             version: a2
             serial: 00:11:d8:ad:4c:59
             size: 100000000
             capacity: 100000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.48 duplex=full ip=192.168.1.47 link=yes multicast=yes port=MII speed=100MB/s

and video:
display
                description: VGA compatible controller
                product: GeForce 6200
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:fd000000-fdffffff iomemory:d0000000-dfffffff iomemory:fc000000-fcffffff irq:201

Hope this helps.

---

### Post by richbarna on 2006-07-05
[QUOTE=tommcd]Try "lshw" (without quotes) in terminal. The output is easier to read.

Hope this helps.[/QUOTE]

That's the way to do it !! "lshw":rolleyes: I've just been searching my command line notes, I knew it was there somewhere.

Nice one tommcd, now I can write somewhere easier to find ;)

EDIT: hanzj, remember to put "sudo" before the command.

---

### Post by tommcd on 2006-07-05
Glad to help. I also have many notes on useful commands. Trying to remember them all when you need them is half the battle sometimes!

---

### Post by taurus on 2006-07-05
Okay, let's try this again...

Your video card is an Intel Corporation 82815 CGC.
Your sound card is an Intel Corporation 82801BA/BAM AC'97.
Your ethernet card is an 3Com Corporation 3c905C-TX/TX-M [Tornado]...

---

### Post by steve.horsley on 2006-07-05
lshw is a great command. But the output is long. You can pipe the output to a file to read later:
**lshw > hardware.txt**
or just pipe it to less (use 'q' to quit):
**lshw | less**

---

### Post by richbarna on 2006-07-05
[QUOTE=steve.horsley]lshw is a great command. But the output is long. You can pipe the output to a file to read later:
**lshw > hardware.txt**
or just pipe it to less (use 'q' to quit):
**lshw | less**[/QUOTE]

Now that's a good tip.

Thanks

---

### Post by glotz on 2006-07-05
[QUOTE=hanzj]So my video card is "VGA Compatible Controller"? If I tell the people that, they might think it's just VGA, and not xVGA (where x is a letter). Please confirm. What kind of info should i tell them about video card?[/quote]

Nobody has [VGA](http://en.wikipedia.org/wiki/Vga)s anymore. Everybody has SVGAs or XVGAs. All of those are called *VGA*s however. (these are monitors)

> 
So when someone asks for the specs of my video card, what is he looking for?

Well, your video card is another story. People probably want to know the make (probably ATI or nVidia) and the model (x800,etc,etc,etc) and maybe how much memory it's got and possibly if it has renderer 2.0 or 3.0 or somesuch feature. Basically just spit out the _exact_ name and let the people google for the details. (these are video cards)

---

### Post by Bartender on 2006-07-05
Here's Intel's home page for that chipset

[http://www.intel.com/design/chipsets/815/index.htm](http://www.intel.com/design/chipsets/815/index.htm)

This one explains the various permutations.  For example, some of the 815 boards came with integrated audio plus 4X AGP slot, and some of them came without an AGP slot.  Anyone looking at buying your PC would probably want to know if you've got an AGP slot or not.  Also take a look at the ICH/ICH2 specs.. ICH2 is better.

[url]http://www.intel.com/design/chipsets/815/familychart.htm?iid=ipp_815chpst+hlght_family&[url]

This one shows you where the 815's fell within that family of chipsets.

[http://www.intel.com/design/chipsets/mature/index.htm?iid=ipp_815chpst+hghlght_compare&](http://www.intel.com/design/chipsets/mature/index.htm?iid=ipp_815chpst+hghlght_compare&)

Sounds like you're using onboard vid and audio.  That's the basic thing to pass on to a potential buyer, but it'd be good to verify whether your board includes an AGP slot for adding a  vid card, and whether your board has the ICH or ICH2 chipset.

---

