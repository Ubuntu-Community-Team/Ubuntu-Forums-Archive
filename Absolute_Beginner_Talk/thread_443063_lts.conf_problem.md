---
title: "lts.conf problem"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by gnosys on 2007-05-14
Hi there I've succesfully installed edubuntu server 7.04, and configured it to boot thin clients, but now I have a litle (HUDGE) problem.

I can boot PII MMX, but when i try to boot a PI 100mhz, the screen freezes and I only can see the cursor.

Is there any problem with my lts.conf file?

I'm using the default configuration, and I've tried various methods..but nothing works..

I also have other problem..clients with edo ram don´t boot..they allways give kernel panic..is that usual?!

Sorry about my english..

Any help would be usefull!

---

### Post by aberry5555 on 2007-05-14
well the PI 100mhz sounds slightly (slightly being a bit of an understatement if Im honest) underpowered, even for Ubuntu. In order to run Ubuntu easily you need about 128 meg of ram for gnome. How much physical ram have you got and what is your swap partion?

Also what do you mean by "edo" ram?

<--EDIT-->

I've googled "edo" and it looks to be a fairly old type of ram, that or quite obscure :S sorry, on that particular section I can be of no help. I have a feeling Ubuntu isn't designed to work with it. However still post back about the other PC

---

### Post by gnosys on 2007-05-14
So the problem might be on the client's hardware?!

On the pII MMX client  I'm using 32MB of ram, and edubuntu runs like a ferrari!:P

But when I try to boot the PI 100mhz with sdram it almost goes to the login screen but when the cursor appears it remains "stucked"..

EDO ram its a very old type of ram that was used on 386 and also on PI...and what I wanted to do was to put this old machines on a library with a LTSP server..the swap on the server is 2gb, and the clients don´t have any kind of storage drives..

---

