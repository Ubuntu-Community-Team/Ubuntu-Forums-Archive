---
title: "Network key"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lk29lk on 2006-12-18
Hey there,

            Does anyone know how to set up a network key? Seems that i had some problems with it...

---

### Post by antharr on 2006-12-18
What kind of router do you have?
Are you using WEP or WPA?
Need more details.;)

---

### Post by lk29lk on 2006-12-18
erm... when I tried to set a network key, an error occured saying that the network password needs to be 40 bits or 104 bits depending on your network configuration. this can be entered as 5 or 13 ascii characters or 10 or 26 hexadecimal characters.

do not really understand what it means... can someone please explain?

---

### Post by wieman01 on 2006-12-18
Read a bit about WEP & wireless security before you go ahead. This will help a lot. Try this to begin with: [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy")

Are you using wireless at all? Or Ethernet?

---

### Post by lk29lk on 2006-12-19
I managed to find out which kind of passwords I can use. However, I still cannot create a network key.  I'm using wireless network.

---

### Post by wieman01 on 2006-12-19
Ahem, what encryption are you using then? WEP or what? WPA? Please be bit more specific...

---

### Post by Ashrael on 2006-12-19
First you should disable all security features, so no encryption, and no mac address blocking.... Then if you get it to work, you at least know that it is possible and all other things work... Aftre that try to secure your network step by step, so first you enter your mac address into your router (if possible) then enter a wep or wpa key,  you can use ascii (all letters and numbers) or Hex (0 to 9 and a to f)... Try to use wpa, it's more secure...


Greets Ashrael

"Umuntu ngumuntu ngabanye bantu" - Xhosa saying.
(People are people because of other people)

---

### Post by lk29lk on 2006-12-19
My default encryption was disabled, and about the mac address, what is it and where do you enter it?

---

### Post by sonny on 2006-12-19
What is you router model/brand?

---

### Post by macogw on 2006-12-19
Don't enter the mac address until after you have it working.  A MAC address is the ID of your wireless card.  If you go into your web browser and type 192.168.1.1 it should probably bring up your router.  If you have a Linksys router, default, the username is admin without a password.  If you click "wireless" there's "wireless security" in there and WEP and WPA options and MAC Address Filtering is probably in there too (if you have NetGear or something else, I don't know what the interface looks like, but poke around a bit and you'll find what you need). 

You have to set your ESSID (name of your home network) in the router.  Tell the computer that's the one to use.  For now, turn off encryption, mac filtering, and network keys.  Can you connect?  If no, you need driver help.  If yes, read the next paragraph.

You want to go to the terminal and 
```
 sudo apt-get install -y network-manager network-manager-gnome nm-applet
```
ctrl+alt+backspace to restart Gnome (you'll have to log in again).  Now, on the router, choose WPA with a Pre-Shared Key (may abbreviate to PSK) and TKP/IP (encryption).  Make up a nice long-ish (a few words, some caps, some numbers, a ! or * or something in the mix) passphrase (yes, passPHRASE) and put it into the router.  Now save the router changes.  In the network manager applet which will now be in the top right corner of your Gnome panel, you want to choose your wireless connection if it's visible, or "Connect to other Wireless Network."  Enter the passphrase.  You should be able to connect now with wireless security enabled and encryption.

If you want to add MAC Filtering for extra security,
```
ifconfig
```
grab the HWAddress that shows up for your wireless card, and put that in the list of allowed MAC's on the router's configuration page.

---

### Post by lk29lk on 2006-12-23
When I tried to go to 192.168.1.1, it doesn't work and then it sends me to [http://search.live.com/results.aspx?q=192.168.1.1&src=IE-Address](http://search.live.com/results.aspx?q=192.168.1.1&src=IE-Address), so what should i do?

---

### Post by vroomfondel on 2007-01-03
This is because he told you to use your network before it was working!
Thats mostly what I read here in answer to "my wifi isn't working.." they tell you to download and install a bunch of stuff of the web ... :p 
How the heck do you do that? Oh, use that windoze pc that was breeze to get working by comparison.

---

