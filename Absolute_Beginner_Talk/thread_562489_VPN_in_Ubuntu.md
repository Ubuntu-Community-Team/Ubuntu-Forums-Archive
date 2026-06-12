---
title: "VPN in Ubuntu"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2007-09-28
I need to set up a VPN in Ubuntu because I am developing an app in python-MySQL to access information from different locations, and have the following questions:

1.  Do I need a VPN Router (hardware), or SSH, or both?
2. While I switch totally from M$ (that is the final goal), can I access the VPN from Windows machines?
3. Where do I find information on how to set it up?

---

### Post by cwmoser on 2007-09-28
I VPN to my Windows PC at work by Network Applet in the upper right-hand corner of the task bar and selecting "VPN Connections".

To access my home Ubuntu desktop from my Windows PC, I use NXServer.  NXServer provides me a GUI desktop like VPN provides.

Carl

---

### Post by CostaRica on 2007-09-28
any suggestions on how to set it up?  Do I need hardware for this?

---

### Post by CostaRica on 2007-09-28
Anybody with knowledge on this?

---

### Post by NilsHG on 2007-09-28
try searching for VPNC
thats what i am using. sorry if i cant be of any more help. i am way overdue for bed. i might find my notes on vpnc tomorrow and will let you know

---

### Post by CostaRica on 2007-09-28
In America (the continent, don't get funny with me :)) is very early!

- Do I need hardware to establish a VPN and get access to a database server?

Thanks for the help!!!

---

### Post by CostaRica on 2007-09-28
I have been searching for VPN in Ubuntu and get software related to Cisco.  Is this free software?

---

### Post by HermanAB on 2007-09-28
Hmm, VPNs are kinda last century and are largely being replaced by ad-hoc SSL connections, of which SSH is a prime example. You'll likely find that any kind of fixed VPN is a pain in the butt to set up and maintain.

I suggest that you install OpenSSL on your machines (Cygwin and OpenSSL on Windows) and use SSH, Konqueror and the fish:// ioslave, or Gftp and Filezilla.

Just my tuppence worth,

H.

---

### Post by CostaRica on 2007-09-28
Thank you, HermanAB.  Can I access my MySQL database through the internet?

---

### Post by bodhi.zazen on 2007-09-28
LOL

Nevermind, misread the OP

+1 HermanAB

---

### Post by cwmoser on 2007-09-29
Install VPN on Ubuntu:

Select System -> Administration -> Synaptic Package Manager

Search for "vpnc"

Select to install these packages:
  network-manager-vpnc
  vpnc


After installation, locate the Network-Manager applet in the upper right-hand corner of the screen - it looks like a double monitor icon.

Left-click the Network-Manager applet.  Under VPN Connections select the option "Configure VPN" then click on "Add". You can now either manually enter the pertinent information or choose to import it via a .pcf file that your IT department may provide. 

I did mine manually this way:

Connection Tab:
--------------------------
  Connection Name:  xxxxxx    <-- whatever text describes the VPN
  Type:  Windows VPN (PPTP)
  Gateway:  nn.nn.nn.nn    <-- enter the IP address for your VPN connection - get from IT department.

Routing Tab:
-------------------
  check "Peer DNS through tunnel"
  check "Only use VPN connection for these addresses"
  Enter the IP address schema that is used by the LAN you want to VPN into.
    Ex:  192.168.99.0/24
    If you don't know, don't check this box.


Ubuntu VPN works great.

Carl

---

### Post by CostaRica on 2007-09-30
> **cwmoser said:**
> You can now either manually enter the pertinent information or choose to import it via a .pcf file that your IT department may provide. 

Carl

This seems like a configuration for your work or something that is already configured at the "server" side, but I need to configure the whole thing myself!  I need to configure a database MySQL server to receive queries from other locations.  Do you know how to  do this?  And, please, do I need HARDWARE to do all this?

Thanks!

---

### Post by cwmoser on 2007-09-30
Maybe someone else can chime in here.  I am familar with how to access Microsoft SQL Server -- which uses OBDC.  With SQL server, I set up a System DSN to point to the server -- Administative Tools - Data Sources (ODBC).  Not use but I suspect that MySQL works similarly. 

Anyone else have comments?

Carl

---

### Post by CostaRica on 2007-09-30
I mean to configure the VPN part of the server; the computer that is going to have the static IP with a VPN tunnel so that the other computers know where in the internet the database is.

---

### Post by mlentink on 2007-09-30
> **CostaRica said:**
>  And, please, do I need HARDWARE to do all this?
Actually, you might.
Not all routers are capable of handling VPN. What brand and type of router will you be using?

---

### Post by CostaRica on 2007-09-30
> **mlentink said:**
> Actually, you might.
Not all routers are capable of handling VPN. What brand and type of router will you be using?

I have an Avaya VSU 500 which IS a VPN router.  The problem is that I can not find in the User's Guide a Linux supported application.

Do you have any suggestion on a Linux-friendly VPN router?

---

