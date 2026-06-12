---
title: "tv tuner"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-31
ok I have an ATI Graphic card
but I also have an ATI TV wonder

how do I find out if it is working

I use to record movies with it from Vista using Catalyst
is there a way to still do that

---

### Post by doorknob60 on 2007-12-31
I googled it, try a program called tvtime. ```
sudo apt-get install tvtime
```

---

### Post by frenchsquared on 2007-12-31
got the program but I dont know if the drivers for the card are installed

---

### Post by MrFSL on 2007-12-31
Here is a link that you might find helpful:

[http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder](http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder)

it lists some known problems and fixes. And I would recommend mythtv for capturing television.

---

### Post by frenchsquared on 2008-01-01
can anyone tell me what all that means
I dont see my tv tuner
and what is all the ram

gordon@Asus:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation Unknown device 003f (rev a1)
00:0a.0 ISA bridge: nVidia Corporation Unknown device 0030 (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP04 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.2 USB Controller: nVidia Corporation MCP04 USB Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation MCP04 IDE (rev f2)
00:10.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:11.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:12.0 PCI bridge: nVidia Corporation MCP04 PCI Bridge (rev a2)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:07.0 Multimedia controller: ATI Technologies Inc Unknown device 4d50
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

