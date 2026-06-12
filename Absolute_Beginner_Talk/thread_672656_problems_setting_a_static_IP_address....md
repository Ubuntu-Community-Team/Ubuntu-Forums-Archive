---
title: "problems setting a static IP address..."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by vamp4life666 on 2008-01-19
I browse the forums and found out a lot about setting a static IP and i think i'm in the ball park, i'm just having trouble finding my seat.

so far ifconfig shows that i have no adrress, which makes sense since the machine is on a private network with no DNS server. I need to set it static so i can webmin to it and map to it with my XP machines.

so far                    sudo nano /etc/netowrking/interfaces/ 

got me

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

other posts say add your IP and mask, but to be honest I'm not sure what this page should look like when i'm done editing... 

any ideas?
MG

---

### Post by Dr Small on 2008-01-19
Here is what my server's interface's file looks like, and it is setup for static IP:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface ath0 inet static
address 192.168.0.70
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid default
pre-up ifconfig ath0 up

```

---

### Post by vamp4life666 on 2008-01-19
originally when i tried i dident sent a gatway and the netmask would change itself from 255.255.255.0 to 255.255.255.255 which was really odd to me....

now with the gatway it is nolonger changing the netmask but i still isnt showing up in ifconfig

---

### Post by Dr Small on 2008-01-19
After you made your interface's file, did you ever restart networking?
```
sudo /etc/init.d/networking restart
```

---

### Post by vamp4life666 on 2008-01-19
i tried that, didn't get me anywhere.

i found a web page that gave me    


sudo ifconfig eth0 192.168.0.x

if i go ifconfig    it shows up as having the right adress but if i reboot the system it goes back to having no adress at all

and now when i go to nano  etc/networking/interfaces nothing is there at all.....lol this is not going very well

---

### Post by Dr Small on 2008-01-19
After you reboot, try:
```
sudo ifup eth0
```

And see if you get an address then.
If you do, you will need to add that command to /etc/rc.local

Dr Small

---

### Post by vamp4life666 on 2008-01-19
i assumed   sudo nano /etc/rc.local

i got 
#!bin/sh -e/
#rc.local#

and some text... where does taht code go in here...

i hate to be so slow but keeping up is a bit more difficult than you may think ....
I was still first cup of ubuntu an hour ago...

---

### Post by RomeReactor on 2008-01-19
> **vamp4life666 said:**
> and now when i go to nano  **etc/networking/interfaces** nothing is there at all.....lol this is not going very well

Hi. Just as a comment, the correct location of the file is **/etc/network/interfaces**; make sure you edit the file correctly:
```
sudo nano /etc/network/interfaces
```
or:
```
gksudo gedit /etc/network/interfaces
```

---

### Post by vamp4life666 on 2008-01-19
i think i may have already screwed up the file


nano...  interfaces   provides me with a blank page

---

### Post by RomeReactor on 2008-01-19
The contents of the file itself are nothing complicated; if the file is empty, add:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.XX
netmask 255.255.255.0
gateway 192.168.0.1
```

This is for a wired connection, correct? What modem do you have (what address do enter in Firefox to access it)?

---

### Post by vamp4life666 on 2008-01-19
that little ing after network was causeing me some problems

question      if i am manually adding the ip, mask, gateway, should i delete "auto eth0"?

---

### Post by vamp4life666 on 2008-01-19
i have tried everything thats been suggested 

oh and ifup eth0 : eth0 already configured

i must say i am less than happy with the wya things are going

---

### Post by RomeReactor on 2008-01-19
> **vamp4life666 said:**
> if i am manually adding the ip, mask, gateway, should i delete "auto eth0"?

No, leave it there. Try rebooting the machine, then run:
```
sudo dhclient eth0
```
And post the output. If this is a wired connection, it shouldn't be that much trouble getting it working. Is this a USB connection to the modem?

---

### Post by vamp4life666 on 2008-01-19
wired to a networking switch that has given me no prblems with any of the boxs i have on it.

Listening on LPF/eth0/ macaddress
Sending on LPF/eth0/ macaddress
Sending on socket/fallback
DHCPDISCOVER on etho0 to 255.255.255.255 port 67 interval 7
..repeats...
..repeats..                   interval 9
..repeats                     interval 8
No DHCPOFFERS recived.
No working leases in persistent databse - sleeping.
michael@imageserver: $

---

### Post by vamp4life666 on 2008-01-19
if i try to ping my laptop which has a manually set address it say unreachable
but my laptop can ping every other machine on my network that i have tried

---

### Post by vamp4life666 on 2008-01-19
where it should have the ip address it says UP BROADCAS MULTICAST 

if that makes a difference

---

### Post by RomeReactor on 2008-01-19
Try [these]("http://ubuntuforums.org/showthread.php?t=40339") [threads]("http://ubuntuforums.org/showthread.php?t=526225"); if they don't help, you might want to post on the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=136") section.

---

### Post by vamp4life666 on 2008-01-19
OMFG....   I was giving up for the evening... Already shuting down my laptop...and I was just staring angerly at the networking switch and I realize the link lights for the port were off... I check to make sure they were tight, they were they were stiff off.

I grabbed another cord the lights came on and i ran throught the sud nano ... steps one more time and and it all came together. Walked to my desk sat down at one of my xp boxes opened IE and was able to login to webmin with the sttatic IP no problems....

The whole time it was the cord.... the cord.... the thing that gets me is that i used the cord just the other day with no problems on my a powerbook g4.   

Grr....     i need a drink...        or some choclate covered ubuntu beans...... 

Thanks for all the help, I honestly was lost a few hours ago but now I know, tommorow when i sit down to set up the other box that also needs a static IP and webmin, I will be able to knock it out in abotu an hour or two with no problems. 

Thanks, again
Michael

---

### Post by RomeReactor on 2008-01-19
No problem; glad you got it working.
Welcome to the forums! :popcorn:

---

