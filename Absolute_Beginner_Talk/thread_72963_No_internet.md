---
title: "No internet"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Vladimirm on 2005-10-07
I dont get internet or sound using ubuntu, is it recomended i should try somethign else, or is there a way to solve the problem?

---

### Post by christooss on 2005-10-07
dial up or dsl

which sound card

Which Ubuntu etc.

---

### Post by matthew on 2005-10-07
[quote=Vladimirm]I dont get internet or sound using ubuntu, is it recomended i should try somethign else, or is there a way to solve the problem?[/quote]
To help you we need a lot more information. The problem might be able to be solved but there is no way to know right now. I can't make a good recommendation for an alternative either without knowing more details about your hardware.

---

### Post by Vladimirm on 2005-10-07
dsl

version 5.04

Not sure which sound card CMI8738 pci 5.1 channels it says on the box

---

### Post by christooss on 2005-10-07
sudo pppoeconf

---

### Post by Vladimirm on 2005-10-07
excuse me?

---

### Post by WikipedianKiba on 2005-10-07
That is a command you enter into a root terminal so it can detect your ethernet. (Please note I am a total newbie too!)

---

### Post by christooss on 2005-10-07
sorry that I wasn't clear

Open terminal

type

sudo pppoeconf

type all asked information and than try ping i don't kno [www.google.com](www.google.com)

to ping just write ping [www.google.com](www.google.com) in terminal.

---

### Post by Vladimirm on 2005-10-07
"Sorry i scanned 1 interface but the access concentrator of your provider did not respond. please check your network and moderm cables. another reason for the scan failure may also be another running ppoe process which controls the modem."
Give up and try another distro??

---

### Post by christooss on 2005-10-07
Did you try to ping ?

---

### Post by Vladimirm on 2005-10-07
Did you mean in the terminal?
I typed ping in on its own adn then came up alot of stuff i didnt understand. this is all new to me

---

### Post by christooss on 2005-10-07
ping -c 3 [www.google.com](www.google.com)

it will send 3 pings

and you should get this output

matic@ubuntu:~$ ping -c 3  [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.93.99) 56(84) bytes of data.
64 bytes from 66.249.93.99: icmp_seq=1 ttl=241 time=64.0 ms
64 bytes from 66.249.93.99: icmp_seq=2 ttl=241 time=79.6 ms
64 bytes from 66.249.93.99: icmp_seq=3 ttl=241 time=147 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 64.073/97.163/147.745/36.330 ms

---

### Post by Vladimirm on 2005-10-07
'bad number of packets to transmit'

---

### Post by christooss on 2005-10-07
hm have you forgoten number three (3)?

---

### Post by Vladimirm on 2005-10-07
*sighs a weary sigh and smiles*
 could you run me through it one more time?

---

### Post by christooss on 2005-10-07
ping -c 3 [www.google.com](www.google.com)

---

### Post by Vladimirm on 2005-10-07
'unkown host'
One day some little sod like me is going ot ask me for some help adn im just going to tell him where to go

---

### Post by christooss on 2005-10-07
Hm

Try this one:

Go to System > Administratons > Networking

and than fill DNS in. Than disable connection i think its ppp0 or something like this. Disable and enable all connections just to be sure :)

Than try ping again. If this doesn't work I really don't know what to do

---

### Post by christooss on 2005-10-07
And ofcourse there is a options file :)

open this file with

sudo gedit /etc/ppp/options

it should look like this
```
# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system
proxyarp
```

Than put a # in front of proxyarp

and save

---

### Post by christooss on 2005-10-07
ups I forgot

you have to run pon command

sudo pon 

in terminal should do

---

### Post by spooky-mac on 2005-10-07
Have you thought already about disabling IPV6? It might be that his connection gets blocked due to IPV6 still being globally active.

---

### Post by christooss on 2005-10-07
And I forgot to ask you do you have router or Firewall between dsl modem and your comp?

---

### Post by Vladimirm on 2005-10-07
cheers, went onto administrator network adn found that the thing wsn tenabled. Im going to pretend i havent wasted everybodys time ok?
Now about my sound....

---

### Post by Vladimirm on 2005-10-07
Anybody? im on top of the world and could do with goinga bit higher

---

### Post by GreenHawkIA on 2005-10-08
To your sound question, this howto fixed all my problems:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by Vladimirm on 2005-10-08
Didnt work. I have no sound at all

---

### Post by Vladimirm on 2005-10-08
it says there are no plugins installed

---

### Post by GreenHawkIA on 2005-10-14
Are you still using Hoary?  If so, try [these instructions ]("http://www.ubuntuguide.org/#codecs")from the guide on for size.
Hope this helps!  It took me a few tries myself but now everything works fine on my laptop.  Just be patient with it and don't stress.  Too much.  :D

---

