---
title: "Issues using hotel wireless"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-05-31
I have no issues what so ever to connect to any network that I have tested unless they comes as a service from a hotel. I can connect just fine but no ip configuration is received but the DNS servers. I can both connect and receive IP configuration when using Windows however. So I tried to statically add it in Ubuntu, the same information that I got but still a no no.

What is it that makes it impossible to do this with Feisty?

---

### Post by kernel tom on 2007-05-31
is it a wired connection?

if so in a terminal type 

sudo dhclient eth0

assuming eth0 is ur wired card

EDIT:::
just saw you said wireless

you may need to know the exact name of the network, or use a client such as wlassistant to connect to it

sudo apt-get install wlassistant

then run

sudo wlassistant

click and connect

---

### Post by MockY on 2007-05-31
I use NetworkManager and it works flawlessly elsewhere, so it is not a hardware issue at all. I think that it does have issues when there is proxy servers involved, but I can't confirm that.

I figured someone else might have had this problem before. If not I guess I can try WiFi-Radar or wlassistant as kernel tom suggested. But why can't NetworkManager work when faced with hotel wireless? It sees the network and connects to it just fine, but does not receive any ip configurations. If it didn't work at all then I wouldn't even be able to do that, and my fear is that this will happen with what ever type of software (WiFi-radar or wlassistant) I use. It works as soon as I go hardwired but not wireless.

---

### Post by hillbilly on 2007-06-01
If any of the wifi application did not allow you to connect, you try the below CLI commands (it maynot work, but its worth a try)
well if the hotel wireless doesnot have a passwd you could try the following:

> sudo iwconfig eth0 essid any
sudo dhclient eth0 
where eth0 is your wireless card and you use "any" if you don't know the network name
If you do know the network name just type it in place of "any"

In case there is a password associated with the network use 
use the option key e.g.
> sudo iwconfig eth0 essid *<network name>* key s:*<ascii password>*

---

