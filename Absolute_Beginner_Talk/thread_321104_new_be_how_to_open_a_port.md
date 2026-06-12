---
title: "new be how to open a port?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by troll380 on 2006-12-18
ok im on a comcast  modem 
and i have no idea how to open the port any hints please?
i dont use a router as this is my only box
thanks

---

### Post by lance_klusener on 2006-12-18
The list of ports that are currently used by your system is in the file /etc/services . You can have a look at that and get the service name .( You can edit this file too)

After you do that "/etc/init.d/service-name start" is the procedure to start the service to use that port

I hope this is of some help

---

### Post by lamego on 2006-12-18
Usually a modem just provides TCP/IP connection to your server, there is no special requirement to open ports...

---

### Post by troll380 on 2006-12-18
ok it is not a"modem" im on comcast high speed
and i dont kown how to open the port i need in this op sys
as im a long time widows user
i can doit there
alitte more help would be nice lol
ok just got  off the phone with comcast they said they only block port 25

---

### Post by JayTee on 2006-12-18
Use Add/Remove programs to install the program named Firestarter from the repositories. This gives you a graphical front end to IPTABLES as a tool to manage your inbound/outbound settings. It's not identical to the Windows firewall you've used but if you're not sure of something there is a help section for it in the manual. You can open specific IP ports for either a specific IP address, all local lan IP traffic or all traffic.
You can do port forwarding as well.

---

### Post by troll380 on 2006-12-18
ok fire starter said im in full stelth mode so how do i get the port open
this is getting fusterateing
need more info as to wath to do ore adiffernt p2p program

---

### Post by troll380 on 2006-12-18
Port 4662 is not available!

This means that you will be LOWID.

Check your network to make sure the port is open for output and input.
how do i fix this please?
this was my first post

---

### Post by JayTee on 2006-12-22
Open your Firestarter program. Click on the policy tab. There are three sections displayed on that tab, Allow connection from Host, Allow Service and Forward Service and a scrollable text box that lets you switch between Inbound Policy and Outbound policy. If you want to allow incoming traffic on that port you add a rule in the Incoming Service section. If you want to allow Outgoing traffic on that port you select Outbound traffic Policy from the box at the top of the pane.

Right click in a blank area of the middle section of Inbound Service and select Add Rule.
A popup window will appear titled Add New Inbound Rule.
The Name box contains names of the commonly used ports and the port numbers that are assigned to them but your port may not be listed by name.
You will need to type the port number 4662 in the Port box. 
There are 3 radio buttons and by default Anyone is checked. 
This is the least safe setting but will ensure that any traffic on that port will pass through regardless of the source address. Save your changes and _repeat the same steps for Adding a Rule after selecting Outbound traffic policy_ from the scrollable menu at the top of the tabbed window.

---

