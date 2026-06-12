---
title: "Screen and Internet"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by White_Sabre on 2008-02-28
Ok, sorry if this has been posted 100 times. I have searched in google and have found posts on how to do this stuff but I havent quite figured it out. Today I installed Ubuntu Linux on my PC. I have Vista installed and eveythings good with that.

Problem 1) Internet Connection, I had a look at some guides and typed in suo pppoeconf, and then orry no working ethernet card could be found. I am using a router an all with USB or Ethernet, But I was trying just ethernet. Nothing, on Vista it works so idk.

Problem 2)Screen Resolution, I have a 19" Screen and it wants a 1440x990 reso but linux doesnt get that high:\ I know theres some command line but that didnt work for some reason.

Anyway thanks if you can help me out. :KS
~Sabre

PICS:
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot.png[/IMG]
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot-5.png[/IMG]
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot-4.png[/IMG]
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot-3.png[/IMG]
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot-2.png[/IMG]
[IMG]http://i196.photobucket.com/albums/aa50/White_Sabre/Screenshot-1.png[/IMG]

---

### Post by superprash2003 on 2008-02-28
is DHCP enabled in the router?? go to system->administration->Network
 you will find a list of network devices- you should see something called wired connection(eth0 or eht1)... click on that and click on properties and change from ROAMING to DHCP if DHCP is enabled in your router.. otherwise manually enter the ip address information!!..also post ifconfig if this doesnt work!!

---

### Post by jan quark on 2008-02-28
first please post the out of these terminal commands to specify the exact model of your network devices
```

lspci
```

```
sudo lshw -C network
```

also read these guides dealing with ethernet connections
[LIST]
[*][https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
[*][https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)
[/LIST]

---

### Post by oedha on 2008-02-28
can you type lspci from terminal
then post here the network and display section
or open terminal and type
sudo lshw -short -C network
and
sudo lshw -short -C display

what's the result ?

---

### Post by White_Sabre on 2008-02-28
Uhm its a Dynalink RTA1320 modem
the first commad just kept saying unknown device except for
Firewire (IEEE 1394) : Agere Systems FW323
second command jsut said alot of random things
 for the first poster theres the Modem connections thing, I try to configure with my connection address and pass, but I have to enter a number to dial for..?
Will get screens 2morrow morn

---

### Post by superprash2003 on 2008-02-28
no.. not the modem connections.. dont you see something called eth0 or eth1?? type ifconfig in the terminal and post results here!!

---

### Post by jan quark on 2008-02-28
> second command jsut said alot of random things

random for you perhaps:)
please just post the output here

---

### Post by White_Sabre on 2008-02-28
Added in Photos of the commands. Be back later

---

