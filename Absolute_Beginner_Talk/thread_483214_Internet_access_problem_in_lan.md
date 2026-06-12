---
title: "Internet access problem in lan"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ran_foru on 2007-06-24
Hi..

Hey i using Feisty . i m connected to  internet through usb and I connected one ohter  laptop to my pc ethenetcard to access the intenet on laptop also but  i am not able to access internet  on my laptop some one help me.

my modem has ip 192.168.1.1 and my pc ip is 192.168.1.188(manually configure)
and the laptop is dhcp configured 


thx in advance for help

---

### Post by punx45 on 2007-06-24
is your modem a combo modem/router?   does it have DHCP enabled?   your laptop wont configure correctly with DHCP if there is no DHCP server running on either of the other two devices.   also, if you are running ethernet directly from one laptop to another you probably need a crossover cable.

---

### Post by BobCFC on 2007-06-24
Yes you want to plug laptop into an ethernet port on the modem so that you can use the laptop without the PC switched on.   

If you cannot do this you might be able to bridge the connection on the PC using brctl and ifconfig commands.   It works for two ethernet connections I am not sure about one USB and one ethernet.

Here is a thread about using brctl automatically on startup

[http://ubuntuforums.org/showthread.php?t=482138&highlight=bridge](http://ubuntuforums.org/showthread.php?t=482138&highlight=bridge)


This assumes you can actually ping the PC from the laptop.?  If not punx45 is right you will need a crossover-cable or a hub or a router to connect the two machines.  Also make sure laptop is on same subnet 192.168.1.x

---

### Post by punx45 on 2007-06-24
oof.. of course, how could i forget bridging?!:-k

---

### Post by ran_foru on 2007-06-24
> **BobCFC said:**
> Yes you want to plug laptop into an ethernet port on the modem so that you can use the laptop without the PC switched on.   

If you cannot do this you might be able to bridge the connection on the PC using brctl and ifconfig commands.   It works for two ethernet connections I am not sure about one USB and one ethernet.

Here is a thread about using brctl automatically on startup

[http://ubuntuforums.org/showthread.php?t=482138&highlight=bridge](http://ubuntuforums.org/showthread.php?t=482138&highlight=bridge)


This assumes you can actually ping the PC from the laptop.?  If not punx45 is right you will need a crossover-cable or a hub or a router to connect the two machines.  Also make sure laptop is on same subnet 192.168.1.x

Hey ..

I have  some confusion  like my laptop and ethernet card of my pc   should be dhcp or manual 

dhcp is disable in modem
thx

---

### Post by BobCFC on 2007-06-24
If you can connect laptop to modem then use dhcp.  If not then do manual on same subnet as pc and try to use brctl to bridge the connections.

---

### Post by ran_foru on 2007-06-25
> **BobCFC said:**
> If you can connect laptop to modem then use dhcp.  If not then do manual on same subnet as pc and try to use brctl to bridge the connections.

Hey 

I dont know anything abt bridge connnection :(:(

---

### Post by BobCFC on 2007-06-25
First step, you need to make sure the Laptop is talking to the PC properly,   See if they can PING each other.   No point trying advanced stuff if you have not sorted the cables out.

Normal network cables are not for connecting two PCs directly.  They plug into Hubs, Routers Switches etc  to connect many PCs.   If you cannot connect both into the modem because it only uses USB then you will need a Hub, Router, Switch or a special cable called crossover cable or twisted pair.  If you cannot afford one you can modify an ordinary cable but you will need to find a tutorial about that.  Basically you take off one plug and swap the wires over I think.  I am a programmer not good at electronics.

---

