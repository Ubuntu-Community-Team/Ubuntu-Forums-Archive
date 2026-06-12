---
title: "i don't know what's wrong !!!!!!!!!!!!"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by AlMaSoUdI on 2006-02-27
when i want install the ftp program this will appear:

[COLOR="DarkRed"]almasoudi@almasoudi:~$ sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd
almasoudi@almasoudi:~$[/COLOR]
 so what to do ??

---

### Post by Rumor on 2006-02-27
1. Use fewer excalamation points in your subject line.
2. Click System -> Administration -> Synaptic Package Manager
3. Enter your password
4. Click Search
5. Type in proftpd
6. Check it off the list that returns and click mark for installation.
7. Click Apply

---

### Post by kaamos on 2006-02-27
Have you done this? [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Consider also using synaptic, makes life easier: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by Gustav on 2006-02-27
Have you enabled the universe repository?

If not, do so by removing the # in the beginning of the line with universe in it in the file /etc/apt/sources.list and then type apt-get update.
EDIT: to late

---

### Post by wisdoms on 2006-02-27
Hi guys, 

ive got the same problem, but worse! I cannot open Synaptic from the "System > Administration". But not only this!!! Also the other items!!! :( :( :( 
What can i do??? I cannot configure anything!
Cheers

---

### Post by LordBug on 2006-02-27
Error messages, please.  Both for Synaptic and anything else not working.

---

