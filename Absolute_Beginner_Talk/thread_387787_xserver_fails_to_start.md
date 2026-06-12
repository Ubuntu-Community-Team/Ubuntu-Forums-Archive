---
title: "xserver fails to start"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by shiningpathb4me on 2007-03-18
This happened several months ago and I couldn't find a solution, so I installed Fedora Core 5, which worked on boot w/out any configuration.

I'm back now, with the latest ubuntu for amd64 and it does the same thing.

every solution I've heard included "press ctrl-alt-F1" to get a terminal.

ctrl-alt-F1 doesn't appear to do anything on my system, and it certainly doesn't give me a prompt.

Does anyone know why this might not work on all PC's? Anyone have another solution?

---

### Post by aktiwers on 2007-03-18
When it fails to load xserver, doesnt it throw you to Terminal mode?
There you should be able to type:
```
sudo dpkg-reconfigure xserver-xorg
```

And reconfigure your xserver.

Or you dont happen to have a Logitech Internet Navigator keyboard? It has this stupid "F-lock" key you need to press first, to activate your "F" buttons.

---

### Post by shiningpathb4me on 2007-03-18
No, it takes me to a blue screen bordered with what I assume are extended ascii charachters, but definitiely not the ones the developer intended. 

In the center it tells me xserver failed to start, most likely because it's not configured correctly. It asks if i want to see the log file. I can choose yes or no. If I choose yes I get the option of seeing a server log also. Neither logfile has anything of any value to me (perhaps a more knowledgeable person would understand the messages).

I have seen keyboards w/ function locks, but mine doesn't have that feature.

I'm going to try again though. Should I be able to hit ctrl-alt-f1 from that blue error screen?

---

### Post by HereInOz on 2007-03-18
After you work through the questions about wanting to see the xserver output and all that, on that blue screen, you should eventually get to a black screen with white text, and that is the terminal screen.

From there you should be able to run 
sudo dpkg-reconfigure xserver-xorg 
and set up your xserver to suit your hardware.

But you have to go through the blue screens with the ascii characters first.  It doesn't matter what you answer to the questions at this point, the main thing is to get to a terminal screen and then log on if you are asked to, and run the command.

If the initial settings you choose fail, have another go and you will get to the point where it hopefully will work.

---

### Post by shiningpathb4me on 2007-03-18
OK - Progress made - Only the left side ctrl-alt keys work, I was using the right side keys!

I worked through dpkg-reconfigure screens and answered all. If I didn't know what to use, I accepted the default.

when finished it put me back at a prompt.

I entered 'startx'

It failed and put me back at a prompt. I paged throught the log file it created. It had a list of 10 zillion video cards in that file. This is what was written at the bottom:

(II) Primary device is: PCI 01:00:0
(II) ATI: Candidate "Device" Section "ATI Technologies, Inc Radeon X800(R430 UO)

(WW) PCI Mach64 in slot 1:0:0 could not be detected

(WW) PCI Mach64 in slot 1:0:1 will not be enabled because it conflicts with another non-video PCI device

(FF) No devices detected
fatal server error 104:

no screens found

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If it means anything to you, the PCI location of the card, 1:00:0 was the default (which I accepted) when I stepped through the configuration program

---

### Post by shiningpathb4me on 2007-03-18
# scanpci -v

[snip]

pci bus 0x0001 cardnum 0x00 function 0x00: vendor 0x1002 device 0x554f
 ATI Technologies Inc R430 [Radeon X800 (PCIE)]
 CardVendor 0x1002 card 0x2160 (ATI Technologies Inc, Card unknown)
  STATUS    0x0010  COMMAND 0x0007
  CLASS     0x03 0x00 0x00  REVISION 0x00
  BIST      0x00  HEADER 0x80  LATENCY 0x00  CACHE 0x08
  BASE0     0x00000000d000000c  addr 0x00000000d0000000  MEM PREFETCHABLE 64BIT
  BASE2     0x00000000fdef0004  addr 0x00000000fdef0000  MEM 64BIT
  BASE4     0x0000ee01  addr 0x0000ee00  I/O
  MAX_LAT   0x00  MIN_GNT 0x00  INT_PIN 0x01  INT_LINE 0x0b

[snip]

---

### Post by shiningpathb4me on 2007-03-18
Update:

I tried setting driver to vesa to see if that would help and it just turned off the monitor when I ran startx. Heheheh

Thanks for the help guys, I'll try back in about 6 months, maybe ubuntu will recognize my ATI X800GT card then. Heading back to Fedoraland . . .

---

