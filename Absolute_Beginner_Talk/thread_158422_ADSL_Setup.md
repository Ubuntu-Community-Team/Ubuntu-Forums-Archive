---
title: "ADSL Setup"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by drowner on 2006-04-11
Hey everyone.


I searched for an answer, but i couldnt get any love :(

So i got a new ADSL connection. I moved house.

I got an ADSL2+ connection. My modem is a Zydel Prestige 660. NOt wireless

So i got windows online by visiting a modem dns address....and configuring passwords etc


tried to do the same with ubuntu, and it didnt allow me. It infact said i was blocked.

Is there another way im supposed to set up the modem?

Thanks guys. You rule.

---

### Post by bonzodog on 2006-04-11
Are you connecting to the modem over Ethernet? I have the a similar model to you, and I configured the modem in windows originally, and when I set up ubuntu, I just told it that I had a DHCP connection to a broadband modem over ethernet, and it found the connection immediately. 
You should be able to access the modem in Firefox by going to [http://192.168.1.1](http://192.168.1.1), where it will ask you for the admin password.
My Modems exact model is the ZyXEL Prestige 623R-T1, and it has both a USB connection (do not use in Ubuntu - requires a driver!), and ethernet.

---

### Post by sapo on 2006-04-11
In some modems you have configure your ethernet card to a certain ip or ip range to be able to access you modem, for example, to acesse my modem i have to set my ip adress to 10.0.0.X otherwise it cant be acessed.

For example, if you modem ip adress is 192.168.1.1 try setting up your computer ip adress to 192.168.1.2 or something like it.

---

### Post by drowner on 2006-04-11
Hmm

Firefox tells me i cant browse to that address. its not alowed.

HOw do i change the computers ip address?

---

### Post by drowner on 2006-04-14
lol

i fixed it.

my eth0 port hadnt been activated :blushing: :blushing:

Occams Razor!

---

