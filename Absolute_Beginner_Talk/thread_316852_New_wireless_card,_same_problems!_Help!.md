---
title: "New wireless card, same problems! Help!"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by pthickett on 2006-12-11
Guys,

After my problems yesterday with my old wireless card, i thought 'what the hell, i will get a new one, my old one was rubbish anyway'. So i got a linksys wmp54g card, obviously ubuntu didnt pick it up properly (or at least i dont think so!) i ran this command so you can see what its details are:

sudo lshw -C network

to get this:

[B] *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@02:08.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:30:78:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=rt61pci driverversion=CVS firmware=.bin link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:eb000000-eb007fff irq:201[/B]

I found this howto about the rt61 card:

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

and only got as far as (d), as when i come to edit the file with my network details (i am running a wep secured network btw) i cant bloomin modify anything! I try and move the cursor with the keys and it types random letters, it seems impossible! i have no idea what to do!

I am a very new ubuntu user, there must a proper dummies guide to doing this because i am so confused! please help me out here guys!

Thanks

Pete

---

### Post by K.Mandla on 2006-12-11
Hi. I've used that guide for the same card, and it should work fine. The reason you're getting wacky characters in step (d) is because you're editing with vi in binary mode. Just using vi can be a nightmare if you're not familiar with it.

When I used that guide I ignored the ralink network setup file and just changed the network authentication settings through the normal location -- /etc/network/interfaces. I think (but I don't know for sure) the only time you would need to use the included file is if you're using WPA.

---

### Post by pthickett on 2006-12-11
oh right, so i shouldnt need to modify that file then? what should i do instead?

should i just skip (d) and copy the rt61.ko driver? and does that mean i can use the gui based network config app like normal?

cheers

Pete

---

### Post by igknighted on 2006-12-11
Instead of
```
sudo vi -b rt61sta.dat
```
try this:
```
sudo nano rt61sta.dat
```
Nano is a much easier editor to use.  If you are in a GUI you could use this too:
```
gksudo gedit rt61sta.dat
```

---

### Post by pthickett on 2006-12-11
Aaaaargh! how irritating! I managed to get it working, and made it get an ip address and got on the web. Even to the point of installing the nvidia drivers i needed and stuff like that. Then when i rebooted it wasnt online anymore. Im aware that i would have to do something to reconnect each time i restart or make up a logon script. However just for simplicity i was going to see exactly what i would need to do each time to reconnect. And now i cant get it back online at all! How far back in the steps do i need to go to get it back on?

Also one other question, i have my display drivers installed, but my max resolution is only 1024 x 768??

Cheers

Pete

---

### Post by ultranoize on 2006-12-11
i also have problems with the rt61. Check out this HOWTO
[http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61)

---

### Post by pthickett on 2006-12-11
I have just had a crack at it, for some reason now i am having more problems... my first of all the bit about creating the headers, i have no idea what that means! also i get as far as the make all command right at the start, and i get an error then, then after that it just goes horribly wrong!

Is this just because i am ubuntu incompetent! its very frustrating, especially seemin as though i had it working for a shorty while, although i cant make it work again!

Any advice would be great, i really dont want to be using XP for much longer... grrr

cheers

pete

---

