---
title: "can't connect to internet in Kubuntu can in ubuntu"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-16
I'm having a problem connecting to the internet on Kubuntu. I've just installed it but it says "unknown host google.com" whenever I try to go online. I am surprised it didn't pick it up automatically, since ubuntu did. 

Any ideas?

I'm connecting straight to my broadband modem via Ethernet cable... It should just work shouldn't it?

---

### Post by Ludford on 2008-01-16
anyone? It's saying something about a bad gateway ip

---

### Post by Ludford on 2008-01-16
Please help!

---

### Post by Hospadar on 2008-01-16
What kind of connection? is it wireless or wired?
The only real difference between ubuntu and kubuntu in terms of network is the network managers they use (i think they actually both use "network-manager" but they use different applets to interface it) 

You could try going into synaptic, uninstalling "network-manager-kde" and installing "network-manager-gnome" I'm not sure how this will work, but give it a try.  then restart the machine and see if you can get your connection happening with the gnome network manager.

Alternatively, depending on your hardware and network setup, we could probably hard-configure your network manually through your /etc/network/interfaces file and dump network-manager all together.  If the first doesn't work for you, come back with your setup and we can try this option.

---

### Post by azad on 2008-01-16
Okay, calm down. I don't use KDE but I know that setting up the network is significantly harder that Gnome.

There are 3 things you have to set in order to get internet working:
1. IP Address
2. Gateway
3. DNS Addresses

Its really easy in Ubutu with Network Manager but Kubuntu has different interface for doing that. Now go to Control Center and check if you've inserted all 3 things.
(I don't know exactly where you need to go but I think you can figure it out.)

---

### Post by Ludford on 2008-01-16
I don't know my IP address gateway or DNS... I've never had to find out.

when I plug the ethernet cable into my xp or mac computer, the network is autoconfigured

I can't install network-manager-gnome either... as I can't get on the internet!

---

### Post by anachreon_ on 2008-01-16
Just curious, but is this a fresh install of Kubuntu Gutsy, or did you install KDE on top of your previous Ubuntu (Gnome) install?

---

### Post by Digger78 on 2008-01-16
to add DNS servers

```
echo 'nameserver [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR]' | sudo tee -a /etc/resolv.conf
```

repeat for each DNS server

not sure if you would need to restart networking 

```
sudo /etc/init.d/networking restart
```

---

### Post by Digger78 on 2008-01-16
you should be able to find out your DNS server addresses from your ISP's website

or

you could try OpenDNS  -  208.67.222.222 and 208.67.220.220

---

### Post by azad on 2008-01-18
Okay. seems like you are on a DHCP network.

You IP address and Gateway will be autoconfigured everytime you boot. But you still have to set DNS addresses. It is usually provided by your ISP. If you don't know what it is go with Digger78's advice.

I'm sure you'll find a GUI for a setting up the DNS.

---

