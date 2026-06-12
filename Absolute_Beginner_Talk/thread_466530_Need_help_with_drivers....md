---
title: "Need help with drivers..."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-06
Hey, recently installed Ubuntu and I'm loving it. But the problem is, I can't get the driver for my integrated graphics card without internet. Is there a way for me go get the drive for "Intel Corporation 82810 CGC" and "Intel Corporation 82810 GMCH" on a CD/USB drive? And by the way, where can I download the driver? :p

---

### Post by benanzo on 2007-06-06
So you are not able to connect to the internet?  Is that a problem with your Ubuntu internet connection or just that you don't have access?

My understanding of those Intel graphics controllers is that they are fully supported in the kernel.  If they weren't you would most likely not have a display at all.  I am wondering if you're asking more specifically about the X.org drivers for the Intel graphics chip.

What graphics are you using?

You can find out by doing this in a terminal ([B]Applications -> Accessories -> Terminal[/B)]:

update the current information for your hardware (if you're connected to the internet):
```
sudo update-pciids
```
Then do:
```
lspci
```

Scroll through the output until you find a listing for the graphics adapter, then post that back here.  We should be able to figure out what driver you need to use.

---

### Post by shamushand on 2007-06-07
> **benanzo said:**
> So you are not able to connect to the internet?  Is that a problem with your Ubuntu internet connection or just that you don't have access?

My understanding of those Intel graphics controllers is that they are fully supported in the kernel.  If they weren't you would most likely not have a display at all.  I am wondering if you're asking more specifically about the X.org drivers for the Intel graphics chip.

What graphics are you using?

You can find out by doing this in a terminal ([B]Applications -> Accessories -> Terminal[/B)]:

update the current information for your hardware (if you're connected to the internet):
```
sudo update-pciids
```
Then do:
```
lspci
```

Scroll through the output until you find a listing for the graphics adapter, then post that back here.  We should be able to figure out what driver you need to use.

```
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:09.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
01:0e.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
```

That's what I get with lspci, and I need a way to download those drivers in Windows and install in Ubuntu, as I have no internet. Weird things that happen because of this card: When I set a panel to transparent, it turns black, and the screen flashes like crazy during bootup/shutdown. Also, any chance of getting beryl or compiz working on this (533Mhz CPU, 256MB RAM, 15GB HD)? :)

Edit: Anything 3D runs very slow at the moment, almost locking up the PC.

---

### Post by shamushand on 2007-06-07
BTW, I don't have internet because I don't have access, only in Windows. Maybe in the future I'll connect Ubuntu. :D.

---

### Post by candtalan on 2007-06-07
> **shamushand said:**
> BTW, I don't have internet because I don't have access, only in Windows. Maybe in the future I'll connect Ubuntu. :D.

Ubuntu is a lot better (safer) to use on the internet than windows, it certainly is worth getting connected if you can. Linux was developed over the internet from the very start, so you will find the internet very useful.

Good luck

---

### Post by NeoLithium on 2007-06-07
The internet would be most beneficial, I believe the package you are looking for is xserver-xorg-video-intel
which is available here [http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel](http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel)

Though we can surely help you get online with ubuntu as well, what type of connection do you have? Do you use a username/password, router, etc :)

---

### Post by shamushand on 2007-06-07
It's a tricky situation, the internet thing...

Firstly, my sister has a computer with the router (Westell 620).
My Windows computer (not a laptop) has a receiver (Netopia 3D Reach).
My sister's PC is in another room, while mine and the Ubuntu are in the same room.

How can I connect the Ubuntu PC to the network? I've heard Linux is incompatible with wireless (which I doubt) from my local CompUSA when I asked for a receiver. How else can I connect it then? The Ubuntu PC doesn't even have an Ethernet port. I've considered hooking it up directly to the phone line then downloading the files, then disconnecting. And worst of all, during the install, Ubuntu said it didn't detect the network card... I'm very n33bish at Linux... I need all the help I can get lol... :p

Solutions I've considered:

1. Take the router from my sister's room, and connect both PC's to it (But then I got to check Linux compatible, it's a Westell 620). Give her the wireless receiver.This would require me to buy two network cards - for the Vista/XP PC and the Ubuntu PC, because neither have Ethernet hubs. Not to mention my room doesn't have a phone jack, so I have to make and extension... 

2. I've heard of Fastcat cables as means to connect two PC's, not sure if it's Internet or file/printer sharing. This would also require me to buy two network cards.

3. Any other ideas? Perhaps easier and more budget friendly that won't cost $60+ ? ;)

---

### Post by hkahwaji on 2007-06-07
Does your laptop that you are using has a wired NIC card. You can always connect via the wire. Just get a CAT5 cable and plug the cable to one of the ports in the router and then the other end should be plugged in to your ethernet port. Ubuntu will automatically notify you that you have gained a network connection. 

Open a terminal session and type the following

ifconfig -a

You will see whether you now have an IP address. Try to ping any site such as [www.yahoo](www.yahoo).

Hope this helps

---

### Post by hkahwaji on 2007-06-07
FYI

Ubuntu does support wireless provided that you have a wireless module in the laptop. Something like Intel, Atheros or Broadcom.

---

### Post by shae on 2007-06-07
If you plan on connecting two computers directly, remember to use a crossover cable (A->B/B->A).  Usually the crossover is taken care of by the router if you are plugging a pc into a router, so most stores only carry A->A cables.  Yes Linux works with most wireless connections.  I am currently on my laptop through one.  Just some chipsets are not well supported or are a real pain to set up.  You might consider buying a cheap router for your room to split the wireless between the two computers.  You can set it up as an access point on your wireless internet and be good to go.

Anyways, if you need help with whatever you choose to go with, UF will be there.

---

### Post by shamushand on 2007-06-07
> **hkahwaji said:**
> Does your laptop that you are using has a wired NIC card. You can always connect via the wire. Just get a CAT5 cable and plug the cable to one of the ports in the router and then the other end should be plugged in to your ethernet port. Ubuntu will automatically notify you that you have gained a network connection. 

Open a terminal session and type the following

ifconfig -a

You will see whether you now have an IP address. Try to ping any site such as [www.yahoo](www.yahoo).

Hope this helps

So far that sounds the easiest... and once again, neither of them are laptops, so will it still work?

---

### Post by shamushand on 2007-06-07
Ok so here goes - neither of the PC's are laptops. They are both desktop PC's. Neither have a Ethernet hub, so I have to buy two network cards. I also need to buy the cable for internet, not file sharing. So here are my questions:

1. What network card is cheap, easily installed, and works reliably with Ubuntu? It must have a Ethernet hub too.

2. What type of Crossover cable do I need to buy? There's Cat4, Cat5, Cat6, which one is fit for internet and is, once again, easy and reliable with Ubuntu? Can I try with a regular phone cable? 

BTW, thank you guys, you've been very helpful so far!

---

### Post by shamushand on 2007-06-07
One more thing... before I fo shell out $60 for internet, is it 100% guaranteed that Beryl or Compiz will work (I don't mind hosing the system in the process)?

System Specs:

533 MHz CPU
256 MB RAM
i810 Card

At least with basic effects (Emerald, Window dragging, flaming windows, etc..) ;)

---

### Post by NeoLithium on 2007-06-07
I doubt that Beryl or Compiz would work with those system specs, they seem a little low on Ram and CPU to do their effects....

---

### Post by benanzo on 2007-06-07
You might get *some* of the effects (no guarantee) but you'll certainly not get some of the GPU intensive effects like Rain.  Also, the flames effect will probably be very stuttery etc. so you might not be able to use it.

It's worth a try though!

If you've got an AGP slot in that machine and a D-SUB (VGA) monitor then you can get an older nVidia card that will certainly handle all the Beryl effects.  Here's a [good one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130039") that's pretty cheap.

Good Luck!

---

### Post by shamushand on 2007-06-07
Are you sure? :( I saw a YouTube video, Beryl with only 8MB RAM. He just didn't have the super spinning cube or transparent windows, but all basic effects were there. That's all I want for now, until I get more PC's and keep building up on this one. :p

Edit: That card seems to be within my budget... But no AGP slot! :(

---

### Post by shamushand on 2007-06-07
I've just though of a probably much cheaper idea - is there a wireless receiver that works well with Ubuntu, hopefully without issues and not very expensive. I'm really start to get eager about this! :p

Edit: How would this card be with Ubuntu? [LINK]("http://cgi.ebay.com/HI-SPEED-54-G-WIRELESS-NETWORK-ADAPTER-DESKTOP-PCI-FAST_W0QQitemZ300118280170QQihZ020QQcategoryZ45001QQrdZ1QQcmdZViewItem")
There seem to be many of these floating around eBay, around $9-10 - perfect for my budget.

For those of you wondering "Why is $60 too much for his budget?" Well, because I made this money by helping out a few neighbors with the Windows Pc's. Now I want to put it to good use and get start with Linux! :)

---

### Post by shamushand on 2007-06-07
Also, how should I download and install the drivers until I get connected?

---

### Post by DougieFresh4U on 2007-06-07
I have the  exact same

dougie@DougiesToyBox:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
dougie@DougiesToyBox:~$ [/B]

I really haven't had a hard time with drivers.
I also got Direct Rendering to work. i have tried Enlightenmanrt (E17) which worked well. I am not a fan of Beryl/Compiz (I don't see the point of wobbly windows etc.) so I haven't tried.
This info most likely won't help but just though I would input:)

---

### Post by shamushand on 2007-06-07
Yeah... I've heard Enlightenment is very fast. I might try it and save my money instead of buying graphics for beryl. Still, how to install these things without internet, including the drivers! :(

---

### Post by shamushand on 2007-06-07
Please... Help anyone? I've got no idea how to install without internet! :(

---

### Post by DougieFresh4U on 2007-06-07
> **shamushand said:**
> Please... Help anyone? I've got no idea how to install without internet! :(

Sorry I can't help on that.:(
Maybe I missed some thing here, Did you install on the same machine as windows? Is it that you have dial-up?
Just trying to understand why you can not get internet on ubuntu but have it on Windows.:confused:

---

