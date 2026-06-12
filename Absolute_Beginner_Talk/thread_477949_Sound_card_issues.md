---
title: "Sound card issues"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Fredinthebox on 2007-06-18
Hi all,

I have and integrated soundcard built into my MSI motherboard (RealTek), and I could not get ubuntu to recognize it (albeit i do not know how to get it to do so), so I plopped in my old Audigy 2 card, which has worked for me before in windoze. 

I still cant get it to get recognized though, i think i have installed the correct alsa packages using synaptic, but still nothing. I am not very experienced though Im not a complete newbie, I can execute simple terminal commands and such.

Im stuck right now and any help would be really appreciated, thanks!

-T

---

### Post by Quintin Riis on 2007-06-19
Run the following in terminal, and reply with the output:

lspci 
lspci -n 
lsmod | grep snd

---

### Post by Fredinthebox on 2007-06-19
>>lspci
00:00.0 Host bridge: ALi Corporation M1697 HTT Host Bridge
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 PCI bridge: ALi Corporation PCI Express Root Port
00:11.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:12.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 60)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:14.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 01)
00:15.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 10)
00:15.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:16.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:16.1 IDE interface: ALi Corporation ULi M5288 SATA
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
05:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

>>lspci -n
00:00.0 0600: 10b9:1697
00:01.0 0604: 10b9:524b
00:02.0 0604: 10b9:524c
00:03.0 0604: 10b9:524d
00:04.0 0604: 10b9:524e
00:11.0 0604: 10b9:5249
00:12.0 0200: 10b9:5263 (rev 60)
00:13.0 0c03: 10b9:5237 (rev 03)
00:13.1 0c03: 10b9:5237 (rev 03)
00:13.2 0c03: 10b9:5237 (rev 03)
00:13.3 0c03: 10b9:5239 (rev 01)
00:14.0 0403: 10b9:5461 (rev 01)
00:15.0 0601: 10b9:1573 (rev 10)
00:15.1 0680: 10b9:7101
00:16.0 0101: 10b9:5229 (rev c7)
00:16.1 0101: 10b9:5288
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:0091 (rev a1)
05:0b.0 0401: 1102:0008

>>lsmod | grep snd
(doesnt do anything)

Thanks for replying!

-T

---

### Post by Fredinthebox on 2007-06-21
I dunno if bumping is allowed here, but bump!

So at least it CAN recognize both sound devices, and thats a big thing for me, but i still dont know how to configure one so it works.

---

### Post by Fredinthebox on 2007-06-30
Bump ><

---

### Post by Tommy James on 2007-06-30
I too have a sound issue.  No sound on boot.  If I adjust the volume with the slide control by the clock it works until I reboot or restart X.  Just hit the volume slide again and it works.

Not ideal, but worth a try.

---

### Post by alienexplorers on 2007-06-30
Why does it look like you have 2 sound cards:

> 00:14.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 01)
05:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

---

### Post by Fredinthebox on 2007-07-03
Because I do. Integrated sound and the Audigy.

---

### Post by bazzer on 2007-07-04
Er, I might well be missing the point here, but when you say 'recognised' what do you mean? No sound? If so, it might be that your system is using the 'other' card to output stuff. I use QAMIX a\s my mixer, with 2 sound cards and they come up in 'tabs' so you can select them.

---

### Post by expatCM on 2007-07-04
Presumably you are wanting to use the Audigy card?  Did you set it to default?

You may want to try this from the command line

sudo asoundconf list

This will give you the names of the cards on the system.

Then 

sudo asoundconf set-default-card CARD

CARD is the name from the list which you want to be the default card.

You can then use alsamixer to adjust the sound settings ....  :)

---

