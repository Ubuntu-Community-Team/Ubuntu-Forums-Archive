---
title: "Configuring my internet connection"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by dgroyal on 2005-07-16
I've installed ubuntu on an oldish thinkpad (t20) and I've got a linksys wireless adapter.  The adapter seems to be working, but I want to choose a different wireless network than the one it's defaulting to.  It's defaulting to something called "SkyWave", which you have to pay for, but I want to use the free WiFi connection available at a local coffee shop.  Where can I choose which wifi connection I want to use?  I've tried everything I can think of (in network admin, etc.) without success.

Thanks for your help!
Dave

PS - So far, I am very, very impressed by Ubuntu.  This is my first experience with Linux.

---

### Post by odin on 2005-07-18
Well the first think you should know is the essid of that palce you want to connect to.That's just the name of the network.

Open a terminal.

You can try with "iwlist scanning" and you will get a list of the networks in the range of your wireless card.

Then you have to  "iwconfig eth0 essid network_name" where eth0 is your network device(interface,card).if you dont know what is your network card called just type "iwconfig".

after that you probably have to do a "dhclient eth0"(again your network device doesnt have to be eth0) if you can get your ip via dhcp.


I hope this helps something but if you need a different explanation ask again and I'll try(my english is not very good so you may not understand everything)

 :oops:

---

### Post by Nequeo on 2005-07-18
You might find it helpful to know that the Network Config tool supports multiple locations. But it's not very obvious.

If you look at the networking program, you'll notice a blank box near the top labelled 'Location'. You can click on that and select 'Create New Location' to, well, create a location. 

*Theoretically* you can create several locations and have different network setting for each. In practice, it's nowhere near perfect.

As for your problem, Odin's instructions should be fine. You can also use the Networking program to configure the card once you use 'iwlist scanning' to find out the ESSID. If you're lucky, anyway. My 11mb/s D-link wireless card at home doesn't seem to support scanning. While the Linksys 54mb/s wireless card I have at work, which I could only get working by rebuilding the ndiswrapper kernel modules from the source - does. *shrug* Welcome to Linux!

This issue is one of many that is being 'worked on' for the next release of Ubuntu in October. So stick it out! We need people like you (and me, for that matter) to say "Why is this so d*mn hard!?". And sooner or later, it won't be. 

Cheers,

---

### Post by damonw5 on 2005-07-18
[QUOTE=Nequeo]You might find it helpful to know that the Network Config tool supports multiple locations. But it's not very obvious.

If you look at the networking program, you'll notice a blank box near the top labelled 'Location'. You can click on that and select 'Create New Location' to, well, create a location. 

*Theoretically* you can create several locations and have different network setting for each. In practice, it's nowhere near perfect.

As for your problem, Odin's instructions should be fine. You can also use the Networking program to configure the card once you use 'iwlist scanning' to find out the ESSID. If you're lucky, anyway. My 11mb/s D-link wireless card at home doesn't seem to support scanning. While the Linksys 54mb/s wireless card I have at work, which I could only get working by rebuilding the ndiswrapper kernel modules from the source - does. *shrug* Welcome to Linux!

This issue is one of many that is being 'worked on' for the next release of Ubuntu in October. So stick it out! We need people like you (and me, for that matter) to say "Why is this so d*mn hard!?". And sooner or later, it won't be. 

Cheers,[/QUOTE]
 There is also a GNOME applet that lets you switch wireless networks. Search in Synaptic for "wireless" and look for a package called "netapplet". Then right-click on your toolbar and add to panel. Choose "network selector applet." 

If it isn't in the list even though you installed it, open a root terminal and tpye "killall gnome-panel". That should refresh the list and it should show up when you try to add it. (This is another area that will hopefully be fixed in the next Ubuntu release called "Breezy Badger").

---

