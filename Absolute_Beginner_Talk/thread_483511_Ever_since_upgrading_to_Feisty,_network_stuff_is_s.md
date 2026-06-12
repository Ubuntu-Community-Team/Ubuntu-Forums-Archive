---
title: "Ever since upgrading to Feisty, network stuff is spotty."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by isionous on 2007-06-24
Hi.  I recently upgraded my dapper installation to feisty, and I've been having some issues.  I am not 100% sure that upgrading to feisty made these problems.  The problems started to appear shortly after my upgrade, and that's the only thing that has changed on my computer to cause these problems.

1) Networking is very spotty.  Sometimes a web browser can load web pages; sometimes a web browser finds the server, but never loads; sometimes a web browser reports "can not find server". Same sort of varied performance when I use synaptic stuff to try to install/update things.  

2) I don't have that wonderful network manager that lets me browse wireless networks and connect to the one I want, even after I explicitly installed network-manager and network-manager-gnome.

Is it possible that network-manager messed stuff up?

I would be open to the idea of wiping everything and doing a fresh install from a feisty cd, but I have tried that, and there is a problem with my laptop's hardware.  Something is wrong with the cd drive interface, such that live cds (I've tried more than one kind) will eventually hang/crash and other fun stuff.  I've even swapped out my cd drive with my roommate's cd drive and had the same problem.

Thanks for the help.

---

### Post by Tinaril on 2007-06-24
Whoa, I'm having pretty much the same problem.

I have a dual-boot machine, with both Windows XP and Ubuntu Feisty. I used to use Dapper and it worked great, then I upgraded to Edgy, and it ran fine (network-wise). But then I went through to Feisty yesterday and my Wi-fi networking just isn't quite the same. It actually managed to work for some hours today, but earlier and then now it's not connecting to my wi-fi router.

I am currently logged in Windows XP and it works fine, which proves that there is no hardware problem. Also, another difference from the previous versions to Feisty is the addition of another network thing in the network manager window. Instead of being only one Wi-fi connection (eth1) and my on-board cable network connection (eth0), there's also this extra Wireless (wmaster0) connection that there wasn't before in the previous versions... I don't know if it's screwing things up, but it's there and I can't remove it.

Thanks, as well, for the help.

---

### Post by Tinaril on 2007-06-24
I've ran lspci, ifconfig and iwconfig to get more data about my situation, I'd be thrilled if someone would be so kind and help me out here. I'm at a loss!

In the attachment is the .txt file with the info I got from those.

I'm pretty certain my problem is with wmaster0, that f'ed up MAC address... Or not, as I'm a great Newbie... But I have no idea what to do next!

---

### Post by isionous on 2007-08-08
<cough>

---

