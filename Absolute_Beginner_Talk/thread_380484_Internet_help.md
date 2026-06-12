---
title: "Internet help"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by kurosawa11 on 2007-03-09
Hey guys, this is my first post and I've read through the stickies but haven't found a solution to this.
I recently installed Ubuntu on a amd2000xp with 512ram and 80gb hard drive. I have a netgear wireless router and i have it connected to my Ubuntu machine through Lan. I tried in terminal the pppoeconf code to some how connect my router but it says it doenst detect my network card. I have built in Lan in this machine and PCI card for network too. I've tried both with the ethernet cable. one has the moden show that its connected (lights up the moden in the correct port) but the built in lan doesnt show any kind of connection to the moden.

---

### Post by Obor on 2007-03-09
I have no idea about wireless but when you connected through the cable you can try (in the terminal)
```
sudo ifup eth0
``` to start the connection and
```
ifconfig
``` to check if its up and running

---

### Post by kurosawa11 on 2007-03-09
Hey, thanx for the reply but neither worked. I got eth0: ERROR while getting interface flags; No such device. 
It's disheartening to use linux :( 
here's some more info. my ISP is aol, my router is a netgear wireless but I'm using it with a ethernet cable. when I type in my routers IP it still gives me message saying I cant connect. 
thanx for any help

---

### Post by dRock1286 on 2007-03-09
> **kurosawa11 said:**
> Hey, thanx for the reply but neither worked. I got eth0: ERROR while getting interface flags; No such device. 
It's disheartening to use linux :( 
here's some more info. my ISP is aol, my router is a netgear wireless but I'm using it with a ethernet cable. when I type in my routers IP it still gives me message saying I cant connect. 
thanx for any help

I'm new too, but I don't think you would use eth0.  I think yours should be ath0 or something like that.  go to the terminal and type lspci or lsusb (depending on what your wireless card is) and find your wireless card in the list.  It should tell you the 'name' to use in this......but I'm not sure.

---

### Post by Obor on 2007-03-09
[Here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") you can find out if your wireless card is supported in ubuntu
and [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") is a link how to use Ndiswrapper if its not

---

### Post by kurosawa11 on 2007-03-09
sorry guys your not reading my post properly. Though the router is wireless I am using it WIRED thought LAN. hope that clears things up

---

### Post by mrmonday on 2007-03-09
Under System> Administration> Networking is your network card listed? is it set to DHCP?

---

### Post by kurosawa11 on 2007-03-09
> **mrmonday said:**
> Under System> Administration> Networking is your network card listed? is it set to DHCP?

in networking I only see the tabs connections, general, DNS, Hosts. where do I go for DHCP or to see my network card?

---

### Post by mrmonday on 2007-03-09
There should be a list of network interfaces, under connections... Isn't there?

---

### Post by kurosawa11 on 2007-03-09
oh right yeah there is. says, Modem connection but it asking for phone numbers for the ISP which i have no clue to and account data, what does that mean?

---

### Post by mrmonday on 2007-03-09
Does it not have 'Wired connection'? This is where your LAN would be... If not then you will need to configue it. I will have a look for how to do this now. Post again if this is the case.

---

### Post by kurosawa11 on 2007-03-09
no it only has Modem Connections. 
thanx for the help, linux feels so unfriendly. good to know the community is the oppersite

---

### Post by mrmonday on 2007-03-09
As I am not sure how you connect to the internet, have a look [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html"). Please don't give up on Linux... It's worth all the effort to start with:) Once it is working though you will be glad you did it:D

If you have any questions, post here and we will try to help you. Good Luck and let us know how it goes:D

EDIT: Link should now work

---

### Post by JakeTFG on 2007-03-09
Document not found.

---

### Post by kurosawa11 on 2007-03-09
that link didnt work. I'm starting to think the pc is broken. I have 2 lan ports and 2 usb and neither seem to work with ubuntu. I'll get a new network card and see how it turns out

---

### Post by Derek Djons on 2007-03-09
To keep it basic you have to know or find out the following:

1) _Are both network ports working?_
You say that only one is being recognized. In that case, to keep things simple connect your machine to the router using the working port.

2) _Previous settings!_
Before you installed, was your network card configured manually or was it getting an automatic IP address (DHCP)?

If your machine is getting an automatic IP address, it should work. If not check System -> Administration -> Networking to see if the network card is enabled (for use).

If your machine's network card was configured for manual use, than you should look up the range in order to configure the network card.

As far as I understand your equipment I don't really see what the PPPoE has to do with this?! PPPoE is for dialing in to your provider, acquiring access to the Internet that way, but it's an very old protocol which isn't hardly being used these days.

---

### Post by mrmonday on 2007-03-10
I have changed the link... It now definitely works :) I put it as .htm instead of .html

---

