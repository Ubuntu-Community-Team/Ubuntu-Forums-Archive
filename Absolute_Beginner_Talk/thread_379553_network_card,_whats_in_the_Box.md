---
title: "network card, whats in the Box?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-08
I have just come back from my local retailer with a network PCI 10/100 ethernet card that was in a unmarked box. I don't know what it is other than it looked the same as another boxed one which stated linux compatable, (Can't remember whart brand) the retailer reconed it was the same as well.
I have plugged it into the socket in the motherboard and booted up. Needless to say the only thing listed in the network settings / connections window is the modem which was there to start with. Any suggestions welcome please. xubuntu by the way.

---

### Post by punx45 on 2007-03-08
go to the command line and enter 'lspci' then paste the output here.

---

### Post by rjfioravanti on 2007-03-08
post the results to 

```

lspci

```

---

### Post by Bachstelze on 2007-03-08
Maybe your card was detected but not configured properly. What about this ?

```
sudo ifconfig -a
```

---

### Post by heatrag on 2007-03-08
it took a while, I had to transfer to another computer using a memory stick:) 

1spci not recognised but the other line ....


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8712 (8.5 KiB)  TX bytes:8712 (8.5 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

it dosn't mean much to me, Sorry

---

### Post by Bachstelze on 2007-03-08
All right, so your NIC is not detected. Paste the output of

```
lspci
```

---

### Post by heatrag on 2007-03-08
if thats 1spci

bash: 1spci : command not found

---

### Post by Bachstelze on 2007-03-08
That's a lowercase L, to **l**i**s**t **pci** devices ;)

---

### Post by heatrag on 2007-03-08
Oh l not 1, I've got to pop out for Half an hour. Speak to you then hopefully.

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
)

---

### Post by heatrag on 2007-03-08
Excellent, I feel like i'm getting somewhere, but  how do I configure frm this info. Not forgetting I'm not connected.

---

### Post by Bachstelze on 2007-03-08
Hm, the network card doesn't appear here. Is that all you get ? If so, are you sure the card is properly attached (bliking LEDs ?)

---

### Post by heatrag on 2007-03-08
there is only one ethernet port on the back no LEDs I wouldn't know how to check it beyond that. It fitted in the slot so I assumed it to be ok. would it be best to right this one off?

---

### Post by heatrag on 2007-03-09
So not giving up I put the card into another slot, lo and behold:

00:08:0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)

It now shows in the network window but i am unable to connect to my D-link router via ethernet with the automatic configuration. The help on the Network settings dosn't respond is that usual? I need help to configure so where should I look. Good fun this I know what PCI and NIC is now with the help of Hymn For Life and Wikipedia.

---

### Post by igknighted on 2007-03-09
does the ifconfig line from before do anything?

---

### Post by heatrag on 2007-03-09
any help? looks bette rthan before.

lo       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Bachstelze on 2007-03-09
Do you get an ethX when running ifconfig ?

---

### Post by heatrag on 2007-03-09
Hi. Looks like eth0 I'm afraid.

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:4F:44:75:CA  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3500 (3.4 KiB)  TX bytes:3500 (3.4 KiB)

---

### Post by zvezdogled on 2007-03-09
it looks good.
now try with command
```
sudo dhclient3 eth0
```
this should get u online.

---

### Post by heatrag on 2007-03-09
Wow it works!

how I don't understand, but it works.

Thanks all.

---

### Post by heatrag on 2007-03-09
I've just restarted (in an abortive attempt to getthe realplayer loading) and I didn't stay connected, is that usual, I don't want to keep going to the terminal to log on. Do I close down with the hibernate to solve this? oh I'm on the ubuntu machine now so no more toing and frowing between computers with the usb stick, phew. 
Bet you thought you'd got rid of me.

---

### Post by zvezdogled on 2007-03-09
you could make a luncher on your desktop.

just right click somewhere on your desktop and select create luncher

And then:

Type: Application in terminal
Name: what ewer you want
Command: sudo dhclient3 eth0
Comment: 

And when u press ok a new icon should turn up on your desktop.
And when you want to go on internet, just double click it and write your password (you have to do it just once each time when you restart your computer).

---

### Post by Bachstelze on 2007-03-09
You'll just need to edit a file to have the interface connect when you boot. 

```
sudo nano /etc/network/interfaces
```

What's in there ?

---

### Post by heatrag on 2007-03-09
I think I'm learning but I'm not sure. 
 
 GNU nano 1.3.12         File: /etc/network/interfaces                         

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

there are ^G ^w etc at the bottom what are they for please?

---

### Post by Bachstelze on 2007-03-09
They are the nano commands. ^ means the Ctrl key so for example, the Search function is Crtl+In your file, before the "iface eth0 inet dhcp", add "auto eth0" - like for lo. Then save the file (Crtl+O, Enter to confirm) and exit nano (Ctrl+X). Your interface should then be connected at startup.

---

### Post by heatrag on 2007-03-09
Like so:

# The loopback network interface
auto lo# The loopback network interface
auto lo
iface lo inet loopback

auto eth0 iface eth0 inet dhcp

iface lo inet loopback

auto eth0 iface eth0 inet dhcp

because I'm not having any luck with it. I promise I'm learning, it's just that I'm a MAC user.

---

### Post by heatrag on 2007-03-09
Hey I sorted this myself. I had a browse on the forum and put a line break between auto eth0 and iface etc. connects on boot now. See I said I was learning. Just got to try and connect to my Mac now.

---

