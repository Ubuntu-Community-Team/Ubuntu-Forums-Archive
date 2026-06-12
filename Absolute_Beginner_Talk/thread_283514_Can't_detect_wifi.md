---
title: "Can't detect wifi"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by rafter72 on 2006-10-24
Hi everybody,
as a new player on linux ground, I am having some problems with my new toy.:confused: 
I setup my Ubuntu :D  and guess what? When I tried to connect to internet, I realised that my wifi wasn't on :-k . Ubuntu wouldn't detect my hardware and therefore I can't connect to internet](*,) I would really appreciate some help( I might also have some problem with my cd/dvd writer -can't seem to find it either-but I am ignoring that so far).
Thanks in advance for your help,

---

### Post by Bachstelze on 2006-10-24
Hi and welcome to Ubuntu :)

Details please, what model is your lappy ? You'll most likely have to install drivers through [Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

---

### Post by PriceChild on 2006-10-24
Does your wireless show up in Networking and its just not configured?

Or does it not even get recognised by ubuntu?

---

### Post by rafter72 on 2006-10-24
I've got Dell 6000 1.5 centrino mobile with intel 2200bg wifi card.
With wireless network router/modem is detected by network manager but when I am on ububtu, my wifi isn't seems to be working!!!](*,)

---

### Post by Bachstelze on 2006-10-24
output of *ifconfig -a* ?

---

### Post by bunnybash on 2006-10-24
i have an averatec 2155 laptop with:
turion mt40 cpu
1.25gb ram
80gb western digital
ati radeon 200m
ralink 2500 wifi

i am trying to use ubuntu 6.06

i can't for the life of me get the wifi to work??  i have spent 5 hours trying, and end up just rebooting and opening up windows.  i really really really want to use ubuntu but this is so hard trying to get the wifi to work, my desktop has the same wifi card and i cannot get it to work either but when i read up on it apparently it is supported in the OS, also Ralink actually have open source drivers...

why the hell is this so hard!!  the hardest part is that once the machines are booted into ubuntu i have no internet access on them...

what should i be doing... has anyone else got the Ralink wifi to work??

---

### Post by rafter72 on 2006-10-24
I'll give a try!!
I'll let you know guys.

---

### Post by Bachstelze on 2006-10-24
|b]bunybash[/b], instructions for you are the same, output of *ifconfig -a* please. And Have you checked on the wiki if your wifi chipset is supported ? If it's not, see the link I posted above about ndiswrapper.

---

