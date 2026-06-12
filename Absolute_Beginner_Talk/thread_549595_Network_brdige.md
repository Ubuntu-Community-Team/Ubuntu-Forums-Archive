---
title: "Network brdige?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by aldenhg on 2007-09-12
Hi all,
I'm trying to get my laptop set up as a network bridge, mainly so I can use it as an AP for my Xbox, but also so I can give other computers internet access through the ethernet port. It's a Dell Vostro 1400 with Broadcom wired and wireless adapters. Everything is working fine in terms of drivers and being able to connect from either adapter, but the bridging of the two has escaped me. Here's a breakdown of what I specifically need:
1: Traffic comes in on the wired adapter, gets sent on it's way through the wireless
2: DHCP on the wired side. This isn't that big a deal, but I'd like to not have to manually set up the IP settings of every comp I hook up.
3: Some easy way of turning the bridge and DHCP on and off. You never know when you'll only have a wired connection available.
For the record, I've already dinked around with bridge-utils and firestarter a bit to no avail. Firestarter seems like it should work, but I get an error saying that the firewall can't be started on the wireless adapter. More details can be provided on request.

---

### Post by str8line on 2007-09-13
Doing Windows Tech support now for a number of years there is nothing that breaks an internet connection faster than an improper Network Bridge.  It would be easier and in the long run cheaper to utilize some network hardware (router or if you modem has a NAT router in it) a hub or switch.  Another option if your heart is set on using the laptop as a bridge, using one of the fine firewall or gateway distros out there my be an option for you.  Clark Connect Community Edition located here ([http://www.clarkconnect.com/downloads/]("http://www.clarkconnect.com/downloads/")) may be a better option to creating the desired effect you are looking for and will add capabilities to your network at the same time.

---

### Post by aldenhg on 2007-09-15
Not really and option. Believe me, I'd love to do somthing that would make more sense, but there are many occasions where using my laptop as a gateway would be advantageous for me. I'm a computer tech, so sticking my laptop between a router and a modem would help me diagnose a lot of things. 
As for the Xbox, running a cable to the router simply isn't an option. The layout of my apartment would preclude that even if all the ports on the back weren't filled up. The last thing I want to so is buy more computer hardware (the girfriend is already fed up with all the cables and blinking LEDs).

---

### Post by str8line on 2007-09-16
I can relate to that, the wife had that evil vein in her forehead when I got our 4th pc to turn into a groupware server.  As for your setup I would strongly recommend using the Clark Connect Community Gateway then.  It will do nearly all that you ask but the config is a little confusing at times but their wiki is pretty complete.

---

