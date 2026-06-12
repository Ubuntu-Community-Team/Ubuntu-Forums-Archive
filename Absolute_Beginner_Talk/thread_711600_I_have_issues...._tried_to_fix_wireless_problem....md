---
title: "I have issues.... tried to fix wireless problem.... made a bigger problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Kasbell4 on 2008-02-29
Hello people who are good at Ubuntu junk.

My name is Kevin. I am a brand new Ubuntu user. I'm starting to get the hang of it.... or so i thought, until the other day i was trying to correct the problem i have with my linksys wireless card wusb54c. Well, after probably screwing up some of the instructions my wireless card still seems to be having trouble, which i'll explain in a second. now the other problem i have is when i try to download anything for install anything i get this message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

my problem with my wireless card is that i get service every 5 min, but i get kicked off very frequently and have to reconnect. i downloaded wifi-radar as somebody told me and the problem is not solved.  

can somebody please help me with these problems? gracias

---

### Post by Kasbell4 on 2008-02-29
ps- i'm running gusty on an acer with an AMD sempron processor... if that makes a difference

---

### Post by glennric on 2008-02-29
The first thing you should try is what apt is telling you.  That is type
```
sudo dpkg --configure -a
```

---

### Post by Kasbell4 on 2008-02-29
thank you, done. now how do i fix the problem i have with the wireless... i've tried doing the recommended steps on the other threads, but none seem to work

do i need to install AND uninstall something? why won't wifi-radar work?

---

### Post by dynamethod on 2008-02-29
if you can find out what chipset your wireless card is, try put that chipset into google like, "yourchipset"+drivers+ubuntu

Then once you get some results for that, try the ubuntu forums but put the driver results from the above search into the ubuntuforums search

See what comes up, for myself the network manager did work out of the box with my wireless adapter but not for long, soon it got an error which seemed to hog all the cpu clocks or something like that anyway

So i had to find out what chipset my wifi adapter is then i found out what drivers Im meant to use(mine was rt73 driver, easy to install, guide around here for it, good  guide)

good luck

---

