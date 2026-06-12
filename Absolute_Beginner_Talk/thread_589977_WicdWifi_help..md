---
title: "Wicd/Wifi help."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Neej Suab on 2007-10-24
I hope one day i can be on the other end of this. But i have yet again another problem. I tried searching the forums and google but can't find anything that is directly linked to my problem. I am using Wep sercurity on my home network. I had Ubuntu installed on my laptop and everything was working just fine at home but i was having a bare of a time connecting at school. Due to the fact that i like messing things up, i decided that i would install xubuntu on my laptop. Mostly to learn, but also just to try it out. So i finish the install and connect to my home router. It works well. I go to school and have some issues, normall. I figure everything is fine. I installed wicd because it seemed a lot better then connecting manually everytime to every network. It worked super well for school. I go home and try to use wicd to connect to my home network and it just hangs at "flushing routing tabe" for ever. I had to shut down the computer. I double checked my wep key and everything and it was fine. the router even showed me as connected, but i couldn't access any of the network resources. I then try to manually connect using the network under system, but after manually setting it up nothing happens. I still cannot access any network resources, internet or other. I Just don't know what to do.

---

### Post by kernel tom on 2007-10-24
I have personally never used Wicd.  but I also run Xubuntu on my laptop and I use it on multiple wireless networks (WEP, unsecured, WPA, WPA2).  I use the Network Manager Applet, that stores all the information in your keyring.  It works great, and is an easy way to configure ur wireless network configurations without manually changing things, and it remembers all your info!  So when I bring my laptop to school, work, or coffee house, it is very easy for me to connect, it automatically remembers the network name at that location.

i believe you can get it using the Add/Remove Applications, but if your a command line kinda user i believe its.

sudo apt-get nm-applet
then to run it for the first time
f2 key, then nm-applet
should run automatically at startup from now on

---

### Post by Neej Suab on 2007-10-25
I learned some new information that may help someone who is more familiar with this. I installed the updated 1.3.4 i think non stable version of Wicd and it now freezes on a different screen it says       . It also tells me it is generating the wpa key when it first starts to connect to the router. I'm not using wpa, why does it use wpa instead of wep, is that just an error on the program writing or is it actually trying to use wpa? if it's using wpa how do i fix that? i will try network manager as kernel tom suggested but i really didn't like network manager when i was using it on Ubuntu. I will tinker more with it and with the new info do some more Google searches.

---

### Post by Neej Suab on 2007-10-27
Ok, i found that if you put the key in quotes it works. But i am still having problems. I find if i use iwconfig to try to configure my connection it doesn't work but after i try iwconfig then wicd works. I think its because wicd doesn't have root accessability. Not sure though.

---

### Post by Neej Suab on 2007-10-29
I figure i'm on my own for this, and if anyone else is having this problem and is watching me ramble on this site, I found that if i just open Wicd, with or without sudo, when it trys to connect it creates another device, So if i Ifconfig it shows the etho0 not connected wlan0 with some connection but not really then there is a wlan0:avahi, and if this last one the avahi is there i cannot connect. But if i then sudo iwconfig wlan0 essid "essid" enc "encryption", the wlan0:avahi goes away and i can connect using Wicd. I tried the standard network manager, but it was even worse off. I couldn't get it working at all. also i just updated to 7.10 and it didn't change a thing with my wifi. Well, i guess i will just have to keep going on with the stupid work around. Thanks for all your help, (sarcasm included if you couldn't tell)

---

