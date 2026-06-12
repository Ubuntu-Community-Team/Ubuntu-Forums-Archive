---
title: "firewall needed for linux ?"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-05-17
i just downloaded and installed the firewall ... firestarter ... i thought its not a bad idea to install it ... ( or is it not needed with linux ?? ) 

with windows i have the sygate firewall and i think there are alot more settings then in firestarter ... ( don't know what to say about that ) 

well ! 

little question !

i have to start firestarter everytime i boot linux ... can anybody tell me how to set it up so it starts automatically at startup ? 
(or does it run in the back .. because i just noticed you need root rights to start it ! 

thanks!

---

### Post by BAshworth on 2005-05-17
I'm not sitting in front of it at this moment, but I remember there being a setting to have it start automatically.  However, even with that setting on, the "systray" icon for it never showed up unless I physically launched the program from the gnome menu.

One way I've found to check to see it it's loaded is during the shutdown procedures.  Just keep an eye out for something similar to "Stopping Firestarter" during the computer shutdown sequence.

---

### Post by Ali_Baba on 2005-05-17
You should have a firewall also in Linux.Firestarter is good but also Guarddog is a good firewall.I like it more,i think it has some more options.Guarddog runs on background all the time :)

---

### Post by Knome_fan on 2005-05-17
1. You don't really need a firewall with a default ubuntu setup. All the firewall does is block access to ports on your computer behind which services could listen. The good thing about Ubuntu however is that it doesn't install any services that listen to the outside by default, so running a firewall isn't really necessary. It doesn't hurt though.

2. If I remember correctly, you can indeed tell firestarter to start the firewall at bootup. This will however not start firestarter itself, but initialise the iptables rules that firestarter creates. Iptables is so to speek the real firewall and firestarter is simply a front end to it. So the firewall is running, the graphical frontend isn't.

Hope this helps.

---

### Post by hiptrop on 2005-05-17
[QUOTE=Knome_fan]1. You don't really need a firewall with a default ubuntu setup. All the firewall does is block access to ports on your computer behind which services could listen. The good thing about Ubuntu however is that it doesn't install any services that listen to the outside by default, so running a firewall isn't really necessary. It doesn't hurt though.

2. If I remember correctly, you can indeed tell firestarter to start the firewall at bootup. This will however not start firestarter itself, but initialise the iptables rules that firestarter creates. Iptables is so to speek the real firewall and firestarter is simply a front end to it. So the firewall is running, the graphical frontend isn't.

Hope this helps.[/QUOTE]

ok this sounds logical ! but since i have not configures any iptables ( i actually have to read what iptables actually are :P ) i guess i don't to worry about the firewall anyway ! :)

thanks alot again :)

---

### Post by az on 2005-05-17
[QUOTE=hiptrop]ok this sounds logical ! but since i have not configures any iptables ( i actually have to read what iptables actually are :P ) i guess i don't to worry about the firewall anyway ! :)

thanks alot again :)[/QUOTE]


Anything a firewall does is actually just a set of rules that the kernel has to follow when allowing packets to enter or leave your system.  In linux, they are called iptables.  You can set them by hand but that is a pain in the ass.

Linux firewall software writes the rules for you.  You just tell it what to do.  Firestarter, as well as most other firewalls in linux run at boot.  The rules are set before the netwok comes up.  That is the only way that makes sense.  

You can put firestarter in your session settings so that it launches on startup, but the systray thing is a pain.

---

### Post by vinthund on 2005-05-18
[QUOTE=Knome_fan]1. You don't really need a firewall with a default ubuntu setup. All the firewall does is block access to ports on your computer behind which services could listen. The good thing about Ubuntu however is that it doesn't install any services that listen to the outside by default, so running a firewall isn't really necessary. It doesn't hurt though.
[/QUOTE]

whai if apps like gnutella, bittorrent or mule working? do I need firewall then or not?

regards


vint

---

### Post by Ali_Baba on 2005-05-18
My opinion is that then you should have a firewall,i dont feel secure without it :) But thats just my opinion.

---

### Post by Knome_fan on 2005-05-18
[QUOTE=vinthund]whai if apps like gnutella, bittorrent or mule working? do I need firewall then or not?

regards


vint[/QUOTE]
No, not really, as you probably want these apps to be able to connect to the net anyway. All you could do with a firewall is block the ports these apps are using, but then the apps wouldn't work.

You can of course install a firewall and just open the ports these apps need (google should help you out on which ports exactly), if you feel like running a firewall.

---

