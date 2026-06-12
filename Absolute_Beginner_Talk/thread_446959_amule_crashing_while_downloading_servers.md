---
title: "amule crashing while downloading servers"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Escozz on 2007-05-17
Hey guys i have a problem with amule on my Ubuntu studio pc.

I Installed Ubuntu Studio today on my home pc. But no matter what i do amule just keeps crashing every time i try downloading the server list. and i would be the happiest man in the world if any of you guys here could help me.

I am not sure about what info you guys need to help me. but because i am a newbie to every thing called linux i hope that you guys can guide me trough this. :confused:


your help is really appreciated

---

### Post by Seisen on 2007-05-17
How did you install amule?

---

### Post by Escozz on 2007-05-18
i installed it trough the add/remove aka. the repository

And i also tried installing it with automatix but it was the same result it keeps crashing when i start downloading the server list

---

### Post by jannevanhecke on 2007-05-18
i hav the same problem

---

### Post by Hallvor on 2007-05-18
Try adding servers manually. You just need a donkeyserver or two anyway. :)

[http://ed2k.2x4u.de/list.html](http://ed2k.2x4u.de/list.html)

After bootstrapping, you can run aMule well without servers. Just connect to Kad, and you`ll be fine.

---

### Post by jannevanhecke on 2007-05-18
i cant connect to kad

---

### Post by Escozz on 2007-05-18
Same to me i can connect to he ed2k network now witch is a good thing but it says that kad is off

---

### Post by Hallvor on 2007-05-18
You need to use the servers for a little while first. Then you can run Kad only if you want.

Click Networks--->Kad. Select bootstrap from known clients. Once that is done, and you are connected, you can disconnect from the servers if you want to.

---

### Post by Escozz on 2007-05-18
well it looks like it is working but nomatter what i search after theres is no sources to download from other than 2 or somthing like that.

---

### Post by jannevanhecke on 2007-05-18
it doesnt work

---

### Post by Hallvor on 2007-05-18
Are you connected to a server now? If you want to use Kad only, try downloading a few files with many sources through servers first, and then try again. I use Kad only now, and see 3,8 million clients and 3,09 billion shared files.

---

### Post by Escozz on 2007-05-18
Well i am connected to a ed2k server and the kad info looks like this (im not sure if i am connected to kad or not)

kademila status: Running
Status: off

---

### Post by Hallvor on 2007-05-18
On the globe on the bottom right, there should be two green arrows around if you are connected to both servers and Kad. If the Kad-arrow is yellow, it could mean that Kad is firewalled, or that you just need more sources from the servers to make it work perfectly (and alone). If the arrow is red, you are not connected.

Kad status should say: Connected

---

### Post by Escozz on 2007-05-18
Its red and says KAD off. so it looks like i dons't work. i have tried the bootsrap button but that didn't change a thing.

---

### Post by Hallvor on 2007-05-18
Sounds like a bug to me.

---

### Post by Escozz on 2007-05-18
Don't know what happend but suddenly kad startet working :S

Anyway thanks for the help Hallvor

---

### Post by Hallvor on 2007-05-18
Great. Kad needs sources from servers to be able to bootstrap. If you had a clean install and few downloaded files/sources, it explains why you had trouble. :)

---

### Post by Escozz on 2007-05-18
Yeah guess... i had just installed Studio today so yeah it was a pretty clean install :)

---

### Post by xmido on 2007-05-18
yes, amule seem to crash when getting the server list. i tried it in 2 different pc's with ubuntu 7.04. amule seem to work fine when i was using ubuntu 6.10

---

### Post by Escozz on 2007-05-21
I think that the bug has bin fixed. because i reinstalled amule today and this time it worked :)

---

### Post by xmido on 2007-05-22
yea it have been fixed, works now for me also :D

---

### Post by cdom on 2007-05-22
KAD Firewalled
     Can anyone tell me when the Kad shows firewall is it hardware (router), or software (Ubuntu).
I'm getting a High ID with e2dk but the KAD does not seem to want to connect. Ports are forwarded etc. So far have tried everything that I can think of. Not the best at Linux, so far. Thanks

---

### Post by Hallvor on 2007-05-22
It is common that KAD shows firewalled at first (assuming you have a fresh install). KAD needs a sufficient number of peers from servers to bootstrap. The problem is usually solved after you have been connected to a server a while and have downloaded a few popular files. Once that is done, you don`t really need the servers, and can use KAD only if you want to. (0% chance of connecting to a fake server controlled by RIAA/MPAA.)

---

