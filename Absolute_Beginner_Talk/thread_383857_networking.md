---
title: "networking"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2007-03-13
help, i cant get connected to my wifi.....i am usally good with this stuff but i just cant seem to get it today *hits head on wall* someone please tell me how to config ubuntu to connect to internet
Edit/Delete Message

---

### Post by Gannin on 2007-03-13
What wireless networking card are you using?

---

### Post by bobplano on 2007-03-13
some wireless cards don't work without the drivers. you might need ndiswrapper. try searching your wireless card's model on the forum and wiki, and if you can't find anything helpful then post what model it is here. wireless with linux isn't usually easy anyway so don't feel too bad

---

### Post by c0d4041292 on 2007-03-13
how do i find out what wireless card i have, and sry....i use to be a  rpo at this till it bricked my last comp so i stoped using ubuntu for a while

---

### Post by gangrelsurf on 2007-03-13
open a terminal. Type lspci. Look in there fore something that looks like a wifi. it will tell you what chip, etc

---

### Post by gangrelsurf on 2007-03-13
assuming you have a pci card....

---

### Post by c0d4041292 on 2007-03-13
well,its internal, btw im 14...lol

---

### Post by c0d4041292 on 2007-03-13
it says not found, so yeah

---

### Post by c0d4041292 on 2007-03-13
maby they have driver on the gateway sight, this is why i hate handme down labtops....cant customize it   /=(

---

### Post by gangrelsurf on 2007-03-13
Did you find out what card / chip you have? If so, yeah look on the gateway site, but don't hold your breath. They aren't real good about linux stuff. in the other hand, they prob didn't make the card

For comparison sake, here is part of my lspci output. The first thing there is my wifi

03:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
03:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
03:0b.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

---

### Post by gangrelsurf on 2007-03-13
sorry, I didn't read some of your posts further up.  What did you type that it said not found?

---

### Post by gangrelsurf on 2007-03-13
Do you know how to get to a terminal?

Saying you do, type like this:

you@yourbox:~lspci >> ~/pcilist

This will redirect everything to a file in your home directory called pcilist. Open that with the text editor, gedit, from the menu, copy it with the mouse and paste it in a post

---

### Post by c0d4041292 on 2007-03-13
02:09.0 network controller: broadcom Corporation BCM4306 802.11 b/g wireless LAN controller (rev 03)

---

### Post by gangrelsurf on 2007-03-13
Bitchin'

Some quick poking around ([http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html)) and it looks like you'll want to use ndiswrapper. Pop open the pacage manager ( System Menu | Administration | Synamtic) and search for ndiswrapper-utils

Also, hum, hope you have another computer. You need the windows drivers for the thing. ndiswrapper lets linux use windows drivers. it was made for wifi.

---

### Post by c0d4041292 on 2007-03-13
sry, to dsy thid but can u like tell me step by step what to do....im so lst in todays world..my bad, lol

---

### Post by gangrelsurf on 2007-03-13
let's see, if you didn't have another computer or other internet access, how would would we be having this discussion? My bad.

---

### Post by c0d4041292 on 2007-03-13
lol, its all cool man... i have lots of das like these, lol i just have alot of em  (like today)

---

### Post by gangrelsurf on 2007-03-13
Ok, if it's step by step it will be easyer for me to tell you how to do it from a terminal. So open a terminal (aplications | accesories | terminal on the menu )

then type:

apt-get install ndiswrapper-utils

When it asks if you want to install it, y then enter

do you have the driver cd for the wifi? Do you have a working windows computer?

---

### Post by c0d4041292 on 2007-03-13
no, cd...i have an open mac but if nessesary i can go kick my lil bro off his comp

---

### Post by gangrelsurf on 2007-03-13
here is a link to an exe version of the windows driver. That's not really what we need. We need a zip

[http://members.driverguide.com/driver/detail.php?driverid=432587](http://members.driverguide.com/driver/detail.php?driverid=432587)

if you click on that, it will say you need an account. Say you have one. user is 'drivers', pass is 'all'. it will say you need a new user name, look for the link to continue anyway near the bottom of the text

I don't have a widows box, so i don't know if this is a self extracting zip or what. You might try running it on another windows box and see if it lets you extract to a folder. that's what you want

---

### Post by c0d4041292 on 2007-03-13
it sayed cant find packedge ndiswrapper-utiles

---

### Post by c0d4041292 on 2007-03-13
well man, don bother.....i guess ill just install a dual boot windows **** just to use firefox and aim...lol

---

### Post by gangrelsurf on 2007-03-13
Well, the gist of it is

1. Get a windows driver for it
2. Get the windows driver, unzipped, into a directory on the ubuntu box ( I usually use /usr/lib/wifi/ , but you can put it in your home directory or whatever)
3. Open a terminal and type man ndiswrapper, and see what you can figure out from that.

Give me a bit to do some studying, like an hour or so, but if you are still stuck then, zap me back

---

