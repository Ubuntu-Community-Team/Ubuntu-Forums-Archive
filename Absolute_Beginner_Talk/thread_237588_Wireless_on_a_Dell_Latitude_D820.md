---
title: "Wireless on a Dell Latitude D820"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by netposer on 2006-08-16
I'm trying to get the wireless working on my new Dell D820 and as far as Ubuntu knows it doesn't exist. I only see my wired connection and my modem.

Can anyone point me in the right direction?

---

### Post by Cryonic on 2006-08-16
I have the same laptop, with Dapper installed, but I haven't used the wireless yet. 
I've gained some experience in wireless troubleshooting with setting up Dapper on my home PC so I'll see what I can do and I'll let you know :)

If you're eager to try some stuff out anyway, follow the link in my sig.

EDIT: ok, I see it's connected to an USB port, so I'm guessing it requires some kind of dongle? Couldn't get it to work under Win XP either.

---

### Post by netposer on 2006-08-16
This is the built-in miniPCI wireless adapter.  I think it's the WLAN 1395 or something (I'll boot into XP and get the correct name).

It's the "Wireless 1390 WLAN MiniCard"

---

### Post by Cryonic on 2006-08-17
It should be this one: 

0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

(This is the last line of the output of "lspci" in a terminal).

So it's not recognized. However, I found a related thread for this device that seems to have a solution:

[http://ubuntuforums.org/showthread.php?t=234869&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=234869&highlight=broadcom+4311)

And even a wiki page about setting up broadcom 43xx devices:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

I'm checking it out and write down the steps in case I get it to work.

---

### Post by netposer on 2006-08-17
I got it working with WEP only following the instructions on this page:
[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

Do I have to do anything else to keep the settings after I reboot?

And is there a way I can use WPA SPK instead of WEP?

---

### Post by Cryonic on 2006-08-18
That does work quite well, I got stuck on extracting drivers from the firmware in another thread. 
This:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

mentions setting up WPA with network-manager.

---

