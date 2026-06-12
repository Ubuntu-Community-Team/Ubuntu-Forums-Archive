---
title: "[SOLVED] Wireless basics"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by alexmoon on 2006-11-29
Background: more or less completely new to linux and Ubuntu, just installed Ubuntu on a dual boot laptop. No "basic" knowledge - I only learnt what "sudo" is a day or two ago.

Problem: I can't get the internet to work. The problem at first was the wireless card, I went and bought a (more easily) compatible wireless card today. In the shop it worked, and for a few glorious minutes I had the internet on ubuntu. Now I'm trying to figure out how to make it work on my home connection, and I can't figure out what I'm doing wrong.

I went into system > administration > networking and put in the details for our network (network name, password, set it to DHCP [I think those are the right letters!]), made sure the box next to "wireless connection" had a tick in it... and nothing. I tried clicking on the network manager (??) on the top right hand of the screen and configuring things through there, but it just takes me back to the same screen as I got to through system > administration > networking.

Someone suggested that I type in "iwconfig", and when I do I get this:

lo      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"DLINK"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-16 dBm  Noise level:-204 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


No idea what to do next, even where to start fiddling. I've looked around everywhere I could, and I'm sure I'm missing something silly, but I have no idea what.

Any ideas where to go from here?

---

### Post by rlozano on 2006-11-29
is your wireless using any authentication, WEP? WPA?

---

### Post by alexmoon on 2006-11-29
I don't know. I've looked around and done a search on the help page and I can't find out a bit on that. When I search on within the "networking" help page I get some stuff on wpa_background and wpa_passphrase things, but I'm afraid none of it makes much sense to me. On my Windows partition I use WEP for my internet connection, I think. (Don't know if that's relevant at all.)

---

### Post by Josh1 on 2006-11-29
> **alexmoon said:**
> I don't know. I've looked around and done a search on the help page and I can't find out a bit on that. When I search on within the "networking" help page I get some stuff on wpa_background and wpa_passphrase things, but I'm afraid none of it makes much sense to me. On my Windows partition I use WEP for my internet connection, I think. (Don't know if that's relevant at all.)

Have you accesed your router on your windows box? wpa_passphrase is the wireless password you have set for your Wi-Fi on your router.

---

### Post by orangemoose on 2006-11-29
You need the WEP key from the router in order to connect to the router wirelessly.

1. Login into the Windows partition.
2. Use the Network wizard. (I can't remember all the steps.)
3. Print SSID (name of the router) and the hexadecimal  WEP key eg.   CA89DE....
4. Logout of windows and login into Ubuntu.
5. System->Adininstration->Networking
6. Wireless connection.
7. Enter the SSID in the Network Name.
8. Password type Hexadecimal.
9. Enter WEP key as the Network Password.
10. Configuration is DHCP.

That's all it took for me on Edgy.
Hope the helps.

---

### Post by Josh1 on 2006-11-29
Does ubuntu only allow WEP? WEP can be cracked into in under 3 minutes.

---

### Post by alexmoon on 2006-11-29
"1. Login into the Windows partition.
2. Use the Network wizard. (I can't remember all the steps.)
3. Print SSID (name of the router) and the hexadecimal WEP key eg. CA89DE....
4. Logout of windows and login into Ubuntu.
5. System->Adininstration->Networking
6. Wireless connection.
7. Enter the SSID in the Network Name.
8. Password type Hexadecimal.
9. Enter WEP key as the Network Password.
10. Configuration is DHCP."

As far as I can tell, I've done this.

I've tried typing in this:
sudo iwlist rausb0 scan
[rausb0 is the name my wireless thingy comes up with, in the network manager (?I think? The little two-computers-graphic on my task bar?)]

I got this:
rausb0 Scan completed:
Cell 01 - Address: 00:0F:B5:78:DC:DA
          Mode:Managed
          ESSID: " "
          Encryption key:on
          Channel:1

Surely it should say something between the two quotes in ESSID?

I've entered my ESSID in the GUI (DLINK), which my housemates assure me is the name of our router, and I've also tried typing this:

sudo iwconfig rausb0 essid "DLINK" key 1password3 mode managed

and this:

sudo iwconfig wlan0 essid "DLINK" key 1password3 mode managed

It didn't seem to do much.

Any ideas where to go from here?

---

### Post by orangemoose on 2006-11-29
That address is too short for a WEP key.  Looks like a MAC address.
I think WEP keys are 16 hexadecimals long.

---

### Post by bluefalcon_ on 2006-11-29
Same exact thing is happening to me.  When I go into Networking, Activate the wireless card, nothing happens, I don't see any SSIDs in the drop down menu.  I have put them in nothing happens.  It worked before on 6.06, but not on 6.1.  I have the same card as this guy RT2500.  When I go into Networking Tools it says unknown device for the wireless network card.

Now, I have looked into this and they say there has been a problem with the card in the past.  Then even have a fix to it, though when attempting the fix it says that this card is supported.  Therefore, I did not continue and assumed he card is supported.

I myself am a newbie to linux, so basically, I am complete lost, but have tried jus about everything and looked in all the documentation I could find.

---

### Post by alexmoon on 2006-11-30
Okay, I took my laptop into the uni computer people, who are quite lovely and have helped me a heap, and they did more things to it. They said I should go through the terminal rather than the GUI, at least until the wireless gets straightened out, and gave me instructions on what to do.

But... it still isn't working. It seemed to work there, but now again trying to use my home network doesn't work.

When I click on the network manager, it seems to say that there's data being both sent and received, but then when I try to use firefox it doesn't work - it says it's connecting, but then the connection just times out.

I have no idea what to try next - any ideas?

(And thanks, by the way, for all the help - I'm finding the Ubuntu/linux community incredibly supportive as a stumble along with all of this.)

---

### Post by bluefalcon_ on 2006-11-30
What exactly did they have you do if you can remember?

---

### Post by alexmoon on 2006-11-30
To do it through the terminal? Ummm...something like:
1. sudo su 
(password)
2. nano /etc/network/interfaces/
3. Then I change over so the "#"s are in front of the details for either my home network or uni network, depending on which one I want to use. [The details being stuff like "mode managed" and the password and all of that - I can go over into my other partition and copy it if it will help.] Save and exit.
4. ifdown rausb0
5. ifup rausb0

And then it should be working. But isn't.

---

