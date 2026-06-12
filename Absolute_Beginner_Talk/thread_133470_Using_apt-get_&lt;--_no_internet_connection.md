---
title: "Using apt-get &lt;-- no internet connection"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bsmaat on 2006-02-20
Hi people... When I, say, want to add repositories (spelling?) i can't because I have no internet connection on my Ubuntu machine. However, I'm trying to network win xp and ubuntu together for internet connection sharing (not file sharing so not samba). I can ping both ways so far. Anyway, I need to be able to add repositories so as to install ie. apt-get install dnsmasq ipmasq

Is there anyway I can download them onto my machine and then put them on a flash disk or something and port them onto my ubuntu machine and install from there. Detailed instructions please, as I'm a complete linux newbie.

Thanks for any help, its appreciated.

---

### Post by SSTwinrova on 2006-02-20
You can get all the files you'd need from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), but make sure you also get any necessary dependencies. On your Ubuntu machine then, you could either set up a local repository (someone else will need to explain how to do this as I'm not sure) or just use "sudo dpkg -i (package name)" in the correct order to get everything installed.

---

### Post by soonindallas on 2006-02-20
what are your connection options ?  you say you can ping both ways, and it sounds like your xp box is the one with internet access - can you bridge the connections to get internet access for ubuntu via your xp box ?

---

### Post by bsmaat on 2006-02-20
Yes thats what i want to do. But all tutorials ive seen on networking windows and ubuntu require some sort of installation which I can't do. If you have any other way, please do say so :) A nice simple tutorial would be wonderful :p

---

### Post by soonindallas on 2006-02-20
prerequisite: a crossover ethernet cable if you are connecting your xp box and ubuntu box with a cable.

follow these instructions on your xp box to set up internet connection sharing.  ignoe the stuff about the client computer as this is your ubuntu box.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;306126](http://support.microsoft.com/default.aspx?scid=kb;en-us;306126)

it seems this activates a dhcp allocator and a dns proxy in xp, so you would make sure on your ubuntu box, in system>admin>networking that you are using dhcp and using 192.168.0.1 as your gateway.

---

### Post by bsmaat on 2006-02-20
Thanks for that, seems simple enough. However, how do I set up the default gateway, as I'm using the GUI and not command line. The textbox is disabled once I select DHCP instead of static ip. Thanks

---

### Post by soonindallas on 2006-02-21
[QUOTE=bsmaat]However, how do I set up the default gateway, as I'm using the GUI and not command line. The textbox is disabled once I select DHCP instead of static ip. Thanks[/QUOTE]

it won't be necessary: it works automagically. when you activate the interface with the GUI a DHCP request will be broadcast on the network.  the DHCP allocator will respond to the request and make its ip address known in the process of allocating an ip to your ubuntu box.

Check on the DNS tab that you have the LAN IP of your XP box in the DNS servers field.

---

