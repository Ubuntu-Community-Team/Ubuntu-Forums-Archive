---
title: "My Wireless Card Always Dissapear"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by skyjuice on 2007-01-03
hi guys this is my first post about ubuntu and now in progress switching from windows to ubuntu. :D

ok actually before this i already solve my problem about Netgear Wireless PCI adapter not recognized in Ubuntu. i already search and manage to detect back my wireless pci from this thread

[http://www.ubuntuforums.org/showthread.php?t=176823&page=2](http://www.ubuntuforums.org/showthread.php?t=176823&page=2)

 but AFTER i RESTART my pc , ubuntu cant recognize back my old setting and my wireless pci card cannot been detect and i need to setup it back from A-Z, anyone know what is the problem and how should i solve this problem?

p/s : long alive linux :-D 

Warm Rgds
faizan

---

### Post by riven0 on 2007-01-03
I've heard network manager helps a lot of people with funky wireless issues. Do you have that installed?:

> sudo apt-get install network-manager

---

### Post by skyjuice on 2007-01-03
thx i will give a try :p tonight

---

### Post by kvonb on 2007-01-03
I just ran into the same problem, I'm not using the wireless right now, but what I intend to do is add the wireless device init commands into "wifi-radar".  You can install it through synaptic, it has a place in one of the option sub-menus for adding a start and stop command, I was thinking of putting this:

```
iwconfig wlan0 essid "NETWORKNAME" mode ad-hoc channel 14
```

You will have to put your init commands in though, not mine :).

I'm not sure if it will work, but it is easy to try.

Regards, KEv :)

---

### Post by skyjuice on 2007-01-05
ok guys i already follow the instruction but when i run this command

sudo apt-get install network-manager

it say that i dont have this software and bla bla bla , where should i download this thing?

and be patient with me coz i just run ubuntu for 3days only :D:o

---

### Post by kvonb on 2007-01-05
Which version of Ubuntu are you using, 6.06 (Dapper), or 6.10 (Edgy)?

If it's dapper then you will have to edit a file:

sudo gedit /etc/apt/sources.list

and remove the "#" from the beginning of the lines regarding "universe" and "multiverse", save and exit then type:

sudo apt-get update

Now try installing again.

If you are using Edgy it is easier, jut look on the menu under System->Administration->Software Sources, and enable Multiverse and Universe then try installing again.

Regards, Kev :)

---

### Post by skyjuice on 2007-01-10
Ok guys here the issues i face 

1) My pc cant connect to internet throught direct connection but need to setup using proxy in firefox before i can connect.
2) because of this issues i think i cant update the list as kvonb suggest. and i got error connection failed
3) i already try iwconfig wlan0 essid protemphq mode ad-hoc channel 14
but if error for wireless request "set essid" (8B1A) : set failed on device wlan0;
operation not permitted.

what should i do? ](*,)

---

### Post by kvonb on 2007-01-11
I may be able to help you with that :).

Forget the wifi radar and network-manager, I found that you don't need them and I  uninstalled them.

Try this:

[http://ubuntuforums.org/showpost.php?p=1974970&postcount=14](http://ubuntuforums.org/showpost.php?p=1974970&postcount=14)

From reading quickly through the post that got your card working, I assume that you are using "ndiswrapper" to provide the driver, NOT the "ath" driver.

If that is the case, the instructions in my other htread above SHOULD help you.  Basically all you would be doing is bypassing the network GUI and doing the work yourself by editing it's config file.  I give instructions to make a backup copy just in case it messes things up.

Oh and of course you will have to put your own settings in, I would suggest trying to omit the "channel" part and see if it works without it.  The reason being that for me it didn't seem to make any difference, just always seemed to go to the correct channel on it's own!

Hope that helps, regards, KEv :)

---

