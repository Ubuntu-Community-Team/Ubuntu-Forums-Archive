---
title: "Help printing from Feisty to Windows"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by SapiensFossor on 2007-06-28
Hi there,

I'm trying to set it up so I can print from Feisty to an HP PSC hooked up to a Windows XP machine (the two computers are hooked up wired to a cable network).

I installed it normally: I checked "Detect LAN Printers", clicked add printer, chose Windows (samba), and proceeded to choose the printer.  It asked for a username/password for the network so I just put username as administrator and left the password blank then it asked for a username/password for the Windows computer I'm trying to print to and I did the same thing.

All seemed good.  But it doesn't work :(

When I try to print something from Ubuntu I can actually hear the printer making the noises like it's about to print (but it doesn't).  I check the printing queue in Windows and there is a job with name "Remote Download Document", status "Printing", owner "Guest", pages "N/A".  But it will stay there forever and will never actually print.

Can anyone help please?  :D

---

### Post by DemonKnightDK on 2007-06-28
I had the same problem. try this

on the XP box:

   1.

      Go to Control panel -> Printers & faxes
   2.

      Right-click on Printer -> Properties -> Ports tab
   3.

      Uncheck "enable bidirectional support"


Works like a charm now. Hope that helps you. (i've been fighting this for two days now.)

---

### Post by SapiensFossor on 2007-06-29
That worked perfectly, thank you so much for taking the time to register and share that with me :)

---

### Post by farish on 2007-06-29
Thank you, thank you!  Ithought I had my printing problems solved, but then had to reload Window$ on my wife's box--could not print till I  found this post!  All is well now!  :)

---

### Post by DemonKnightDK on 2007-06-30
you guys are welcome. I had to go through so much trying to find that answer my self. I know I've registered here before but nothing would let me sign in so I just a made a new account. 

I've got a new problem now though, I cant get apt to or the updater to download updates. The auto updater tells me there are updates but it wont down load them :( routers suck, when windows was handling the trafic it just worked ;)

---

