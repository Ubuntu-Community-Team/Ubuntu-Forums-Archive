---
title: "Wireless Hopeless"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by VIKTOR10 on 2007-02-08
Hello everyone.  I am an ablsolute beginner and totaly lost.   For the most part, I must admit everything is running smoothly.  I love the GUI.  I can install and run programs with no problems.  I was even able to install Opera, but could not remeove firefox because other programs depend on it.  Not sure what programs, but I only use a web browser as I read all my mail on web based servers.  That aside, I was not able to get my wireless card working on my Notebook.  MSI270.  It could not see my wireless card...  I swapped Hard Drives back to Windows and noticed it died. Not sure if I did it trying to get drivers to work or not.  It was working until I swapped Hard Drives.  I had a spare mini PCI card, but I lost the BlueTooth from my MSI card.  Well, the new card was picked up right away by Ubuntu.  It came from an old Dell Laditude D610.  It sees the card, but the card does not see my wireless net work.  When I swap hard drives, Vista connects instantly.  So to sum up, How do I make this work?  Any help with this will be very welcome.  This is the only thing that keeps me from switching to Ubuntu on my notebook.

  Thanks for reading.

---

### Post by username132 on 2007-02-08
I might not be following correctly, but you say your card is recognised only, as in you've not yet installed the necessary drivers? Apparently, you'll need a propgram that wraps around your wireless card driver (designed to run on Windows) so it can communicate with Ubuntu. Try following this tutorial: [http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=415&highlight=wireless](http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=415&highlight=wireless)

---

### Post by dannyboy79 on 2007-02-08
well, you really need to find out what chipset your wireless card uses before you can really start following any guides. please post your lspci -v and look for something that states something like this:
0000:05:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
 Subsystem: Netgear: Unknown device 4b00
 Flags: bus master, medium devsel, latency 168, IRQ 9
 Memory at 16000000 (32-bit, non-prefetchable) [size=64K]
 Capabilities: <available only to root>

i posted mine as an example. I am lucky, as this card is supported by Dapper out of the box. so go to a terminal in ubuntu, and type in sudo lspci -v and paste the output info for your ethernet controllers. if you have 2 of them, then post them both unless you can tell the difference between the wireless controller and the ethernet port controller.

---

### Post by VIKTOR10 on 2007-02-13
Thanks for all the Input.  I've not had time to thinker with anything right now as I spend a lot of time working on other things, such as roof tiles, floor tiles...  Painting,.. etc.  Long story short, I haven't looked in to any of your suggestions, I just wanted to post my graditude for your responces.  I've gotten used to my Notebook attached to a life line.  It's not so bad since I moved my router to my bed room.  Since I keep my Notebook pluged into an outlet,..  the extra wire bothers me little.  So long sotry short.  I'm content with it working the way it does.  Other than that, I'm really likeing Ubuntu.  Now if I could just figure out how to delete firefox,..  I'll be one happy camper...

---

