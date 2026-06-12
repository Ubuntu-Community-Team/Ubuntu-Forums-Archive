---
title: "wireless"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-29
my brother in law has just told me that this wireless thing people can look at what your doing on your computer and he said  that i should have somthing or some sort of encrytpion to stop these people 
looking at what you have on you computer, the modem/router im buying is, linksye 354g, what do you think,
and i have not got my new linksys just yet, i think it will be after new year somthing like 5/1/06 when i will
get it, thanks

---

### Post by boomerian on 2005-12-29
Not to worry, Richard. There are encryption methods (WEP or WPA, or something like that) to prevent freeloaders tapping into your wireless network.
That having been said, I have yet to set up (in my recently installed Ubuntu machine) the wireless adapter to work with my wireless router, (both of which worked fine with XP) however there are plenty of forum entries that seem to explain the process well and whose instructions I will follow. (ndiswrapper needed in my case...)
I do think its amusing that many of the install procedures for wireless internet access involve downloading (apt-get) from internet urls. Isn't that what they'd call a "catch-22?"
Cheers,

---

### Post by prizrak on 2005-12-30
Hmm well no one can actually look at your computer w/o a certain amount of skill and wireless won't be your main concern at that point ;) 
WEP encryption is completely and utterly useless it takes about an hour to bypass it. When you get your router you will need to configure it.
1. Change the administrative password.
2. Change SSID to something obscure like "mahwifi" anything will work
3. Enable WPA encryption on the router you will need to enter a password I suggest getting some kind of a password manager that will generate a random password for you and keep it encrypted I like this one [http://keepass.berlios.de](http://keepass.berlios.de) 
4. Grab wpa_supplicant from the repos and configured it (the guide is on the forum)
5. Turn MAC address filtering on and set it to only allow the computers you want on the network. 
I also suggest limiting a number of DHCP clients to the amount of computers you will be running off of it that alone will stop a casual user who connects by accident. All the other things I mentioned will deter everyone but the most skillfull who will care enough to break in. Some suggestions for general wireless use though, don't do anything you want kept private over wireles. E-banking, buying stuff online, other stuff you don't want people to have. It's generally a good idea because the information while encrypted still gets sent out over basically radio waves and anyone can grab it. I do believe that WPA decryption takes a lot of time and effort but its still a good idea to not give more of a chance to the wrong element :)

---

