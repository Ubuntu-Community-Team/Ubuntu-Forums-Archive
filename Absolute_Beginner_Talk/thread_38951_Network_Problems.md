---
title: "Network Problems"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by ajsadler on 2005-06-02
OK so I finally got my dual boot of Ubuntu/W*nXP working.  \\:D/ 

So now I have a new problem. I have a network adapter as I (or we) have a network hub at home and I need to install the Ethernet Adapter Drivers.

On W*nXP I would go about it like this:
Add New Hardware Wizard
Direct the wizard to my CD drive

The location of the driver is:

" E:\net8511.inf "

Can someone help me please? Thanks


-AJ

---

### Post by cwaldbieser on 2005-06-03
Are you sure you need to actually install drivers for Ubuntu?  For most ethernet cards, the network support is built right in.  I have only really had problems with some newer wireless cards, and I still manage to get them to work (though with some difficulty).

What kind of network card or network adapter do you have?

If it is a typical ethernet card, your system may have already detected it.

The graphical programs you use to configure it depend on whether you are using Gnome (Ubuntu) or KDE (Kubuntu), but you can use the terminal on either.

From the terminal, if I type:

```
$ lspci | grep [eE]thernet
```

I see:

```
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)
```

This is my ethernet device, which is recognized by the system without me having to really install anything special.

---

### Post by ajsadler on 2005-06-03
So ...  :???: ... what do I actually do ? Thanks


-AJ

---

### Post by ajsadler on 2005-06-03
Anyone please? Thanks


-AJ

---

### Post by somuchfortheafter on 2005-06-03
your etherenet driver should already be installed if we are talking about linux, also inf files will not work here sorry. to begin you first need to tell us if the card is listed at all, to check (assuming you are in hoary) select the sytem menu up top, then administration then networking. (at this prompt enter in your user password) your ethernet adapter should be listed there and you should be able out how to configure it from here on out. if your still having trouble post back.

---

### Post by ajsadler on 2005-06-03
Linux can 'see' my Ethernet adapter which is a good sign, and it recognises it as Belkin F5D5050 (which is the type of adapter). Using my Windows DOS prompt I did an 'ipconfig' and gathered the information on my IP address, Subnet Mask and Default Gateway.

IP Address - 192.168.0.7
Subnet Mask - 255.255.255.0
Default Gateway - 192.168.0.1

So I booted up Ubuntu once again and went into System>Admin>Networking and on the Ethernet Connection already there, found disactive, I opened the properties and put in the information previously gathered, activated the connection, opened Firefox, but still failed to find an Internet page. Can anyone better describe the method to get my internet working please? Thanks


-AJ

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=ajsadler]
So I booted up Ubuntu once again and went into System>Admin>Networking and on the Ethernet Connection already there, found disactive, I opened the properties and put in the information previously gathered, activated the connection, opened Firefox, but still failed to find an Internet page. Can anyone better describe the method to get my internet working please? Thanks
[/QUOTE]

So far so good. Sounds like you don't need drivers. After you have done all of this, reset your interent source (your modem) with it deactivated. Then try to activate it again.

---

### Post by ajsadler on 2005-06-03
I dont really want to reset my Modem so can I just unplug the USB cable (for my Ethernet adapter) out and plug that back in again? Thanks


-AJ

---

### Post by somuchfortheafter on 2005-06-03
hmm is your windows box set to be dhcp? or does it have a static ip, if it has a static ip.... idk try inputing the values and REBOOT EVERYTHING NO WHINING lol jk but seriously it has helped in the past...

---

### Post by ajsadler on 2005-06-03
OK then I will reset everything and come back to you :) Thanks


-AJ

---

### Post by ajsadler on 2005-06-03
Well it still doesnt work ... 

I deactivated the connection
Reset my computer
Unplugged my network hub
Unplugged my ethernet adapter
Booted Ubuntu
Plugged in my ethernet adapter
Plugged in my network hub
No internet
Reset my computer
Booted Ubuntu
No internet

Are there any particular preferences on Firefox that I need to set? Because I think the internet access is fine because I did that mouse, keyboard, sound, network test thing and the pings went OK. Thanks


-AJ

---

### Post by somuchfortheafter on 2005-06-03
go back to the neworking thing and add your default gateway as one of your dns choices then try it again...

---

### Post by ajsadler on 2005-06-03
I just did that, can I verify, is that via

System>Admin>Networking>DNS Tab
Add
192.168.0.1 (My Default Gateway)

Thanks


-AJ

---

### Post by ajsadler on 2005-06-03
Still having problems, can anyone help? Thanks


-AJ

---

### Post by cwaldbieser on 2005-06-03
OK, you already gave us the output of ipconfig from Windows, which is good.  Now from Windows, do

```
C:\> route print
```

and post the output.  Then boot into Ubuntu, open a terminal, and post the output of these two commands:

```
$ ifconfig
$ route
```

Also, is it just Firefox that isn't working, or do you have no Internet connectivity at all?  Try a

```
$ ping www.yahoo.com
```

or something similar to make sure it just isn't a setting in your browser.

---

### Post by ajsadler on 2005-06-03
Pinging yahoo.com failed.

Ubuntu:
$ ifconfig

eth1
link encap: ethernet
hwaddr: 00:02:1b:00:50:78
inetaddr: 192.168.0.7
bcast: 192.168.0.255
subnet mask: 255:255:255:0
inet6addr: fe80::205:1bf:fe00:5078/64
scope: link
UP broadcast multicast MTU: 1536
metric: 1
RX packets: 49 errors, 0 dropped, 0 overruns, 0 frame
TX pacets: 5 errors, 0 dropped, 0 overruns, 0 carrier
collisions: 0
txqueueren: 1000
RX bytes: 3131 (3.0 KiB)
TX bytes: 378 (378.0 b)


$ route

kernal IP routing table
destination  gateway  genmask  flags  metric  ref  use  iface
192.168.0.0      *   255.255.255.0  U       0        0     0    eth1
default     192.168.0.1   0.0.0.0     UG      0       0      0   eth1



WindowsXP:
ipconfig

connection specific DNS suffix: 
ip adderss: 192.168.0.3
subnet mask: 255.255.255.0
default gateway: 192.168.0.1


route print

interface list
0x1 ... MS TCP loopback interface
0x2 ... b2 0b bb 7d a6 6F ... mac bridge miniport - packet scheduler miniport

active routes:
network destination   netmask   gateway   interface   metric
0.0.0.0    0.0.0.0    192.168.0.1    192.168.0.3    10
65.54.157.113    255.255.255.255    192.168.0.1    192.168.0.3    10
127.0.0.0    255.0.0.0    127.0.0.1    127.0.0.1    1
192.168.0.0    255.0.0.0    192.168.0.3    192.168.0.3    10
192.168.0.3    255.255.255.255    127.0.0.1    127.0.0.1    10
192.168.0.255    255.255.255.255    192.168.0.3    192.168.0.3    10
224.0.0.0    240.0.0.0    192.168.0.3    192.168.0.3    10
255.255.255.255    255.255.255.255    192.168.0.3    192.168.0.3    1
default gateway: 192.168.0.1


Now can anyone help? Thanks


-AJ

---

### Post by cwaldbieser on 2005-06-03
Can you at least ping the router (192.168.0.1)?

The fact that ifconfig said you got some errors:

> RX packets: 49 errors, 0 dropped, 0 overruns, 0 frame
TX pacets: 5 errors, 0 dropped, 0 overruns, 0 carrier

is a little bothersome, but I am not 100% certain what that means.  Possibly, it is normal, though I didn't notice any errors when I did the same thing.

The other things I noticed that struck me as somewhat odd:

1) Your ethernet device is eth1 instead of eth0.  Do you have another network card?  This isn't really a problem, but it just seemed out of the ordinary to me.

2) In Ubuntu, ifconfig says your IP address is 192.168.0.7.  In Windows, it was set to 192.169.0.3.  I'll have to check back over your posts to see if you are using dynamic or static IP addresses.  If you haven't mentioned it before, please let us know.

What kind of router are you using?  Is it set up to only allow traffic from specific IP addresses?

If I can think of anything else, I'll post later.

---

### Post by cwaldbieser on 2005-06-03
OK, I didn't see anything about whether you were using static or dynamic IP addresses in the earlier posts.  When in Ubuntu, try this:

```
$ sudo ifconfig eth1 down

$ sudo ifconfig eth1 192.168.0.3 netmask 255.255.255.0 up
```

Now if you do an ifconfig, you should see that your address is 192.168.0.3, just like in Windows.  Maybe that will help.  If so, then we can set that up in the system network configuration.  If not-- we'll try to think of something else.

---

### Post by ajsadler on 2005-06-04
Dammit this is getting really annoying now.

I cannot ping the router (192.168.0.1)

I have another inactive Ethernet connection which leads to nowhere (eth0)

I've entered that code you say.

I did a ifconfig and it now says 'inetaddr: 192.168.0.3'.

I'm not sure whether it's static or dynamic, how do I find out?

I'm using a Belkin Netgear router.

Internet doesnt work. I reset. Still doesnt work.

Please I really need help and it's stressing. Thanks


-AJ

---

### Post by somuchfortheafter on 2005-06-04
hmm your ifconfig shows that you are not getting a gateway address..try it with dhcp, then reboot your machine and try again...

---

### Post by cwaldbieser on 2005-06-04
No need to stress out.  Sooner or later, whether you are running a Mac, Linux, Windows, or a C64, everyone runs into these kind of problems.  Eventually, a solution presents itself.

Your address is static if your computer's configuration is set up to always use the same IP address.  If your PC is set up to use DHCP (Dynamic Host Configuration Protocol), that means it asks for some centralized agency to give it its IP address from a range.  For example, in my setup, I have a router that is configured as a DHCP server.  When I boot up my PC, the router gives it its address.  Since there are only a couple computers on my home network, I pretty often get the same IP address anyway.

You can probably see how you are configured from the GUI somewhere.  If you type:

$ cat /etc/network/interfaces | less

You can see the file that describes how your network interfaces are configured when you boot up.  If your eth1 device has a line like:

```
iface eth1 inet dhcp
```

it is getting its IP address from the router.  If it is

```
iface eth1 inet static
```

It is being set up with a static IP address at boot time.

I am curious about your router.  I am wondering if there was maybe a CD or something you had to put in your Windows PC when you were first setting up your network?  That could have made some configuration settings on both the router and in Windows that matched.  
Do you have the model number for the router?  I'll try to look up the product sheet online and see if there is anything interesting in that.

---

### Post by ajsadler on 2005-06-04
Well I recently reformated my computer, and for Windows all I needed to do was to Copy over the Driver file from the CD came with the router. The driver only works for Windows, however.

I will try the 

$ cat /etc/network/interfaces | less

command line and see what comes up. Thanks


-AJ

---

### Post by ajsadler on 2005-06-04
Well it says:

iface eth1 inet static
Destination 192.168.0.3
Netmask 255.255.255.0

---

### Post by cwaldbieser on 2005-06-04
Well, that says you are using a static IP address of 192.168.0.3.  That is a little weird, because earlier, ifconfig reported you had IP address 192.168.0.7.

Anyway, you might try switching to using DHCP and see what happens.  In Windows, check and see if you are using DHCP there, first.

Conveniently, the product manual for your ethernet adapter describes this in some detail.  Here is a link to the online PDF version:

[http://web.belkin.com/support/download/downloaddetails.asp?file_id=199](http://web.belkin.com/support/download/downloaddetails.asp?file_id=199)

If you go to page 10, the top dialog shown has an "IP Addresses" tab.  There is a radio button there that can be set to "Obtain an IP Address Automatically" or "Specify an IP Address".  Find out which one yours is set to.  The "Automatic" setting implies DHCP.

---

### Post by cwaldbieser on 2005-06-04
OK, in Ubuntu:

+ System -> Administration -> Networking

+ Enter your password when prompted

+ You will see a Network Settings dialog

+ On this dialog, is the default gateway device set to eth1?

+ In the main panel of the dialog, select the eth1 device.

+ Click the Properties button on the left.

+ Under Connection Settings there is a Configuration drop-down.  It can be set to either DHCP or Static.  Try setting it to DHCP.

---

### Post by ajsadler on 2005-06-04
Wow cheers everyone for all the help I've finally got it sorted. Turns out it is a dynamic address but I needed to reset the router & my computer to get it working which is what I apparently didnt do before. Thanks again


-AJ

(might be a new thread open in a bit with my next problem, but - c'est la vie)

---

