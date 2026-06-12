---
title: "[SOLVED] problems accessing  router"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jfluet on 2007-12-15
hello, i am a newbie to Ubuntu and i am runing 7.10 GG
i have a Netgear RP614v2 router which i got from a friend. i configured it by entering the IP address in the web browser(Firefox) 192.168.0.1useing DHCP the first time i did this it seemed to work fine and when i went to play some online PS3 it wont connect to the router. so i went to try again and i cant seem to access the router at all. i don't know if i did something to the manual configuration or what. but i seemed to try everything i know. if any one could help me with this it will be greatly appreciated!

---

### Post by mike_g on 2007-12-15
You could check your interfaces in the terminal by typing 
```
ifconfig
```
Then check your IP and subnet mask to make sure youre on the same subnet. If they look wrong try staticaly assigning it something like:
```
sudo ifconfig eth0 inet 192.168.0.2 netmask 255.255.255.0
```
Assuming you are connected by ethernet. Don't know if thats any help.

---

