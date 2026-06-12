---
title: "network question"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by vinthund on 2006-01-08
hello,

I know that title of my question is not too informative, however - i did not knoe what sholuld I call it.

anyway, I have been using ubintu for some time but I was never interested in any networking issues since I used just to turn the machine on or plug the wire in and it just worked. Therefore I do not know much about it and my question may be imprecise.

I would like to lend my other machine (with ubuntu on it) to my friend and this is where the problem might appear since she has a different provider. AFAIK they have a kind of network in a multi-flat house and whenever she had to format her XP machine there was no networking unless some guy came and typed some numbers somewhere:P Well, that is what I have been told. Does this mean that there is no automatic IP recognition (something called DHCP?) and she has to enter it manually? If so - how to do it in ubuntu 5.10?

And one more thing - at my laptop I am using ubuntu too. I have two strange however not really serious problems with it.

1. when I switch between windows and ubuntu I have to restart (unplug from mains - you know, electricity) my modem SB 4200E, motorola, otherwise there is no networking. My desktop (which I intend to lend) never requires this.

2. on ubuntu startup (5.04) there is something called "networking configuration" or so (after hotplug system) well, I had no problems with it untli I took my machune to a library where apparently some services (like p2p) were disabled - and that is where this startup-network-configuration started to take a lot of time, like a inute or so. well, afres I came home from the library - the startup time still remains loooong, unlike befor.

Any tips? Thanks in advance.

vinthund

---

### Post by kairu0 on 2006-01-08
[QUOTE=vinthund]I would like to lend my other machine (with ubuntu on it) to my friend and this is where the problem might appear since she has a different provider. AFAIK they have a kind of network in a multi-flat house and whenever she had to format her XP machine there was no networking unless some guy came and typed some numbers somewhere:P Well, that is what I have been told. Does this mean that there is no automatic IP recognition (something called DHCP?) and she has to enter it manually? If so - how to do it in ubuntu 5.10?[/QUOTE]

It sounds like your friend's network is using static addressing instead of dhcp (=automatic addressing.) You can insert those numbers (addresses, more correctly) from the Gnome panel: click System -> Administration -> Network, then click on your network card and push Configure.

[QUOTE=vinthund]1. when I switch between windows and ubuntu I have to restart (unplug from mains - you know, electricity) my modem SB 4200E, motorola, otherwise there is no networking. My desktop (which I intend to lend) never requires this.[/QUOTE]

This is normal and there is nothing you can do to fix it.

[QUOTE=vinthund]2. on ubuntu startup (5.04) there is something called "networking configuration" or so (after hotplug system) well, I had no problems with it untli I took my machune to a library where apparently some services (like p2p) were disabled - and that is where this startup-network-configuration started to take a lot of time, like a inute or so. well, afres I came home from the library - the startup time still remains loooong, unlike befor.[/QUOTE]

At what part of the boot does it stall? At the library, it might have been the Time Synchronization that slowed down the network initialization. At your home, it might be the same thing or something else.

---

### Post by vinthund on 2006-01-08
thank you for your reply.

[QUOTE=kairu0]It sounds like your friend's network is using static addressing instead of dhcp (=automatic addressing.) You can insert those numbers (addresses, more correctly) from the Gnome panel: click System -> Administration -> Network, then click on your network card and push Configure.[/QUOTE]

So instead of DHCP (as I have it) I should choose "static IP" and then enter the addresses in three frames below? I do not need to do anything in  DNS tab?

[QUOTE=kairu0]
At what part of the boot does it stall? At the library, it might have been the Time Synchronization that slowed down the network initialization. At your home, it might be the same thing or something else.[/QUOTE]

At "configuring network interfaces" - after that all works, that is networkin is fine. What I find strange is that I never experienced it prior to my visit to library. That may be a coincidence, but maybe not?


m.v.

---

### Post by kairu0 on 2006-01-09
[QUOTE=vinthund]So instead of DHCP (as I have it) I should choose "static IP" and then enter the addresses in three frames below? I do not need to do anything in  DNS tab?[/QUOTE]

You will need to enter the DNS information, too, yes.

---

