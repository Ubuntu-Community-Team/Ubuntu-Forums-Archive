---
title: "noob's noob wants to network to XP machine"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by ukemike on 2006-06-25
When I say noob's noob for networking I really mean it!  I've never owned more than one PC so I really have almost 0 networking experience at all.  

I've just spent the last hour and a half of my life fruitlessly searching this forum and the official documentation the the wiki etc looking for instructions for how to network between an XP machine and this ubuntu machine.  I have found a few things that looked helpful but don't get me there.  

Both computers are connected to a linksys router and the internet works fine on both.  I have the XP machine setup so that some folders are shared and the printer is shared.  I have installed samba on the ubuntu machine.  I went to System-Admin-Networking-General and called this pc "ubuntu" and the domain "mshome".  I have continued fiddling while writing this and just now I've seen something new.  Under Places-Network Servers-mshome I see my XP machine listed!!! Way cool but when clicking on it I get this message, "The folder contents could not be displayed"

So having gotten that for I have now disabled ZoneAlarm completely on the XP machine.  I can see shared folders and files on the XP machine.  So I guess I don't have an ubuntu issue anymore but a zonealarm issue. 

So here is where I stand.  I can add "sites" to my trusted zone on zonealarm.  But I need to know the IP, and I have this set up to dynamically assign IPs.  So any advice?

---

### Post by acht on 2006-06-25
dont call yourself a n00b
its annoying

---

### Post by aysiu on 2006-06-25
[QUOTE=acht]dont call yourself a n00b
its annoying[/QUOTE]
As opposed to your post?

ukemike, I apologize for acht. Most of the users here are quite helpful to new users.

I don't know if I can help, as I'm quite the novice, too, when it comes to networking. My router I think also assigns IP addresses dynamically, but I think as long as I haven't unplugged any cords, the local IP addresses are relatively stable.

If you want to find out your IP address in Ubuntu, in the terminal type ```
ifconfig
```

I've found *smb4k* to be a good graphical frontend for Samba in KDE. In Gnome, you can just type ```
smb://###.###.###.###
``` (with # being the #s in the IP address) to access the other share.

---

### Post by acht on 2006-06-25
its just that every time someone new posts they go "omg im a n00b" "help a n00b out"  "i is hardcore n00b"  its just not necessary.

---

### Post by RandomConjecture on 2006-06-25
I'm a big fan of whatismyip.com. No need for the terminal, even! Right now I'm running DHCP, and it does change every now and then. Like, when I reboot, unplug cables, lose power, etc. You might consider changing to a static ip setup. It's actually pretty easy, you just have to edit your /etc/network/interfaces file. Change a few words. (Mostly, dhcp to static, although there's slightly more to it.) There's probably a way to do it graphically in kubuntu or ubuntu...I dunno, I run Xubuntu.

---

### Post by jimrz on 2006-06-25
[QUOTE=ukemike]When I say noob's noob for networking I really mean it!  I've never owned more than one PC so I really have almost 0 networking experience at all.  

I've just spent the last hour and a half of my life fruitlessly searching this forum and the official documentation the the wiki etc looking for instructions for how to network between an XP machine and this ubuntu machine.  I have found a few things that looked helpful but don't get me there.  

Both computers are connected to a linksys router and the internet works fine on both.  I have the XP machine setup so that some folders are shared and the printer is shared.  I have installed samba on the ubuntu machine.  I went to System-Admin-Networking-General and called this pc "ubuntu" and the domain "mshome".  I have continued fiddling while writing this and just now I've seen something new.  Under Places-Network Servers-mshome I see my XP machine listed!!! Way cool but when clicking on it I get this message, "The folder contents could not be displayed"

So having gotten that for I have now disabled ZoneAlarm completely on the XP machine.  I can see shared folders and files on the XP machine.  So I guess I don't have an ubuntu issue anymore but a zonealarm issue. 

So here is where I stand.  I can add "sites" to my trusted zone on zonealarm.  But I need to know the IP, and I have this set up to dynamically assign IPs.  So any advice?[/QUOTE]

ukemike,

Try going into your router and looking for an option to reserve and assign specific ip addresses to specific machines by the combination of computer name and MAC address. I use this in lieu of actual "static" addresses (does not work out with network-manager, which I need on my laptop). This works quite well with my Netgear router and leaves my laptop acquiring addy via DHCP, so I do not have to change it in order to connect to other networks. I set up a Lynksys for a friend a while back and believe that it had the option, too. Sorry, since it wasn't needed and I did not use it on that occassion, I don't remember where in the menus it was. Should not be too hard to locate.

---

