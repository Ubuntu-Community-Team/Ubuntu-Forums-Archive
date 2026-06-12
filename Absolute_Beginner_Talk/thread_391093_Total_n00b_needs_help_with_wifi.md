---
title: "Total n00b needs help with wifi"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by sidneylopsides on 2007-03-22
Hi there folks, I've just made the jump to Linux and I'm totally befuddled.
I've got Ubuntu Ultimate I downloaded yesterday, I've installed it on a machine as follows:

VIA N10000 nano ITX board (1GHz C7 CPU and S3 graphics)
300GB SATA
Sony DVD+/-RW
Wiress keyboard thingy
Belking 54G USB wireless adaptor

I've installed it and it's running, but i have no idea how to get the wireless working. 

I've got this up so far:
[[IMG]http://img460.imageshack.us/img460/2401/screenshotiz3.th.jpg[/IMG]](http://img460.imageshack.us/my.php?image=screenshotiz3.jpg)

Can anyone point me in the right direction?

---

### Post by gameman12 on 2007-03-22
ok, first off, can u get on the internet?
second, are you using encryption on you'r router
and third, can u post the output of

```
  sudo ifconfig

```

btw, if network manager is pre-installed in ubuntu ultimate (i have no experience with ultimate) i have learned that net manager will be able to configure what is DISABLED in your network settings

---

### Post by ComplexNumber on 2007-03-22
what about if you switch to wireless connection (wmaster0)?

---

### Post by sidneylopsides on 2007-03-22
1) Nope
2) Nope
3) Took a photo of it:
[[IMG]http://img459.imageshack.us/img459/4043/dsc01300ee5.th.jpg[/IMG]](http://img459.imageshack.us/my.php?image=dsc01300ee5.jpg)

---

### Post by gameman12 on 2007-03-22
sry, can we try this code as well?

  sudo lsusb -v

and


  sudo lshw

  sudo lshw -businfo

---

### Post by sidneylopsides on 2007-03-22
Here we go, quite a bit longer so here's a text file :)

---

### Post by UpsideDownFace on 2007-03-22
I have a Lenovo R50e laptop, with Ubuntu 6.06. I updated to 6.10 and then changed back because 6.06 has "Long Term Support" and I want stability, not the latest bugs.

I went into "System", "Network settings", highlighted  "Wireless connection" and clicked on the "Activate" button.

In "System", "Network Tools" I chose the wireless "Network Device", which is "Ethernet (eth1)" on my machine and clicked "Configure"

I chose "Application", "Accessories", "Terminal" and typed at the command line what is between the quotes :-
~$ " sudo ping -c 3 [www.google.com](www.google.com) "  
after I gave it my personal password I got the following response :-


PING [www.l.google.com](www.l.google.com) (66.249.93.104) 56(84) bytes of data.
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=1 ttl=244 time=42.9 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=2 ttl=244 time=43.0 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=3 ttl=244 time=44.3 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 42.996/43.455/44.345/0.673 ms

I use Firefox for browsing and Thunderbird for e-mail, but the default progams under "Applications", "Internet" worked as well.

I have a small network of my own, and pinged my other computers first.
If "ping localhost" doesn't work then your network card isn't yet working.

I did all this about a year ago and so I may have forgotten some of the details, but is generally right.
There are other useful commands, like "sudo ifconfig -v" which will give information on what you have working for networking

---

### Post by gameman12 on 2007-03-22
ok, i'm using windows right now so ur txt file got mangled 'cause of notepad. :) so i couldn't make heads nor tails of it.

from what i have just read, ubuntu does not support belkin usb wireless devices out of the box.  

this means you will have to use ndiswrapper to allow linux to properly use ur wifi adapter. ndiswrapper allows you to run windows drivers in linux. i had to use this for a built-in dell wifi card which uses a broadcom chipset (also unsupported by ubuntu). 

do you have any internet access at all?

---

### Post by dhtseany on 2007-03-22
Ok dude first does your router have a WEP or WPA key enabled?

Second, it appears that your wireless got an IP addy. Did it get it automatically (DHCP) or did you set it yourself?

If your router is open access (which is a no no :) ) then you should be able to just click the properties of your wireless device (mine in eth1), Check "Enable this connection" then select your wireless network's SSID (name) and hit "OK" (or if you have a WEP Key copy and paste is into the "WEP Key:" field and make sure hexidecimal is selected.) Change your default gateway to "eth1" (whatever the name is for your card) and then hit "OK". 

Let me know if that helps.

Sean

---

### Post by gameman12 on 2007-03-22
that can't work. his wifi adapter is unsuported he needs ndiswrapper

---

### Post by dhtseany on 2007-03-22
Then what is the wireless device "wlan0"? It looks to me like it detected it just fine.

Maybe I'm wrong or I'm missing something.

Sean

---

### Post by dhtseany on 2007-03-22
>  i had to use this for a built-in dell wifi card which uses a broadcom chipset (also unsupported by ubuntu). 


hmm thats odd i have a broadcom built-in wifi chipset and it picked mine up just fine ;)

---

### Post by gameman12 on 2007-03-22
lucky....

:wink:

it can "see" the device but has no drivers to configure it properly. the same thing happened to me when i had to use ndiswrapper for my device.

i'm pretyy sure

---

### Post by dhtseany on 2007-03-22
Ahhh ok then that makes sense. I was seeing it in his net properties so I think that might have been it.

:)
have a good night

---

### Post by gameman12 on 2007-03-22
u to

:)

---

### Post by moffa on 2007-03-22
It seems like his wireless card is detected to me.

Please install network-manager and network-manager-gnome (if you use gnome/ubuntu) or network-manager-kde (if you use kde/kubuntu).

It sets up encryption and works pretty well except that you have you manually connect every time you turn on your computer.

---

### Post by sidneylopsides on 2007-03-23
I tried typing in all the network stuff so that's why there is an IP, its back to DHCP
I'm using my main machine to access the internet, having to use a USB memory stick thing to copy files across.
I turned off all encryption as I thought that might be making things harder.
There is something installed called "Windows Wireless Drivers" that asks me for the .inf file, I've installed that now.

---

### Post by gameman12 on 2007-03-23
that's good, aparetnly ubuntu ultimate has done most of the work for you by installing the visual portion of ndiswrapper as well.

 i believe you also need the .sys file and they have to be in the same directory.

---

### Post by toddhd on 2007-03-23
If you are using WPA-PSK security, then see this post:
[http://ubuntuforums.org/showpost.php?p=2326503&postcount=16](http://ubuntuforums.org/showpost.php?p=2326503&postcount=16)

---

### Post by ComplexNumber on 2007-03-23
>  There is something installed called "Windows Wireless Drivers" that asks me for the .inf file, I've installed that now.
if i remember correctly, you have to put the inf and the sys file in the their own directory somewhere in your home directory. assuming that you have aready installed ndiswrapper,  fire up the commandline and type in the following whilst you are in the same directory as where the "inf" file is:
sudo ndiswrapper -i <name-of-driver>

for example, i was using rt2500.inf, so i entered:
**sudo ndiswrapper -i rt2500.inf **
this will install the driver for you.

you can check to see if you have installed it by typing in:
** sudo ndiswrapper -l** (note: i know its hard to see, but that is a lowercase L).





[this]("http://www.ubuntuforums.org/showthread.php?t=383466") guide may help you from there. 
i have had a look in the Tutorials & Tips sections, and here are a selection of threads that may help as reference:
[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper)
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper) (this is specifically for broadcom)
[http://www.ubuntuforums.org/showthread.php?t=265284&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=265284&highlight=ndiswrapper)




btw i'v only just this minute found out that there is actually a GUI for setting up ndiswarpper. its called  **ndisgtk** and its in the repositories. i don't know if thats supplied on the  ubuntu ultimate disk.

---

