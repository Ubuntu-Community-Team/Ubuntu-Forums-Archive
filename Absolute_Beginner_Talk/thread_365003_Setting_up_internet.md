---
title: "Setting up internet"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by aggierandy on 2007-02-19
Howdy,

Completely new to Ubuntu and Linux. I was having loads of trouble with one of my girlfriends old computers and I didnt have a windows disk so I decided to try a shot at Linux. I installed Ubuntu 6.06 without a hitch and got to play a little bit. I tried to connect to the internet (and by that I mean I plugged in the ethernet cable and opened Firefox.) 

After that failed I went to these forums (obviously not on that computer) and found some "directions" and followed these directions. 
[INDENT]
1. Click System, and navigate to the Networking button. This is where you will enable the connection. It will ask for your password, so input your user password.

2. You should see several selections for using the internet, all currently disabled. We want to enable the Wired Connection, so highlight it and click properties on the right hand side.

3. Another box should come up, everything grayed out except a little checkbox that says "Enable this connection", so check it and make sure the configuration is set to DHCP, unless you have a static IP (if you don't know what that is, use DHCP). Close that little box

4. Now next to the highlighted 'Wired connection', there is a little box, click it until you see a check mark in it. Close the Networking Box.

5. You have successfully enabled your wired connection, so now you want to use it. At the top right of the screen is the button to shut down your computer. To the left is a little computer icon; you want to double click it. The "Name" it shows should be 'lo'. Change 'lo' to 'eth0' (or possibly eth1).

6. Try connection to the internet! Hopefully now you will have a connection if everything is plugged in.[/INDENT]

Except there was no "little computer icon". Instead I went to Networking Tools and saw "lo" and tried to switch it to eth0 but everytime I close it, it just goes back. I am so lost. All I really need to do is get on the internet. I also have a WMP54G PCI wireless card but I have even less of an idea of how to try to set it up. :(  

Thanks in advance to everyone for putting up with my ignorance!

---

### Post by islander_810 on 2007-02-19
K, first things first, do u have a static ip or not? In other words, has ur ISP provided u with a permanent IP address, Default Gateway, DNS Server Addresses and stuff like that?
If yes, then the DHCP option won't work

---

### Post by aggierandy on 2007-02-19
No. I dont believe so. I am connected through my router which is on its default settings and connected to an XP computer. Sorry my level of technical expertise is very low!! Any advice on what to do next??

---

### Post by zvacet on 2007-02-19
After all that work did you type 
> pppoe

---

### Post by zvacet on 2007-02-19
After all that work did you type in terminal
```
pppoe
```
After that look this[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with 

 Exec=gksudo tkpppoe



Sorry for double post

---

### Post by aggierandy on 2007-02-19
ok tried the link and when I type :

wget -c [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

it returns with:

--19:47:32.. [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)
         => `rp-pppoe-3.8.tar.gz'
Resolving  [www.roaringpenguin.com...failed:](www.roaringpenguin.com...failed:) Temporary failure in resolution.



I dont really understand what that was supposed to do. I knew it wasnt gonna work based on the fact that it had a web address in it! So lets try something else. Any other suggestions. Thanks again for being so patient with me! This cant be this hard. Its a simple internet connection

---

### Post by aggierandy on 2007-02-19
Just wanted to thank everyone that tried to help. I just restarted the thing this morning and POOF it worked. So  thanks again.

---

### Post by zvacet on 2007-02-19
I&#7743; glad that is working.In the furure if you have trouble with conection type in terminal 
pon dsl-provider.Try download rp-pppoe from here:[http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe]("http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe")
After download follow the procedure from adress I gave to you.Of course if you want to or if you will need it.

---

