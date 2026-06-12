---
title: "Problem with wifi connection"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2007-01-11
Hi!

I've got a problem with my wifi connection. I'm using Kubuntu 6.10 and Asmax 511G card (Texas Instruments ACX 111).

It looks like everything should be ok. There's a small utitlity that shows wifi networks and it finds my network without any problems. But I cannot connect to it ("Connection failed"). There's no encryption or anything like that set on the router. There's only filtering by MAC address.

In Win XP it works without any problems and with everything set to auto (DHCP is enabled on the router). The error message - "Connection failed" - doesn't say much, so maybe you have an idea what can be wrong?

---

### Post by g0nzo on 2007-01-11
I'm not sure what happend, but it suddenly started to work. I tried setting static IP address in System Settings->Network settings for wlan0 interface. I even disabled eth0. Didn't work. Then I tried Internet->Wireless Assistant Wireless LAN Manager. It found my network, but kept telling that it can't connect. The strange thing is that sometimes, when tried to connect, it was saying that I'm already connected. I entered static IP here again, gateway, netmask etc. Still couldn't connect.

Then I run "sudo dhclient wlan0" and it said that I got IP address from DHCP server (I tried to run it before, but there was timeout). The strange thing is that I entered static IP everywhere and I got dynamic IP address from DHCP different from that static one I assigned manualy. Good thing is that it works, not sure if it will work after reboot though.

Hope that wifi configuration will be simpler in next releases :)

---

### Post by PatrickMay16 on 2007-01-11
Strange... Even though it's working now, it might be a good idea to look through the output of dmesg to see if anything looks odd.

Hey, man... could you help me out? I also have an ACX111 based wifi card. So I'm interested in asking, how does it work for you, now it's working? Does it work fast? Also, if you have any SMB file shares on your network, does it skip if you play an mp3 file which is on a network share on one of your other computers?

---

### Post by annda on 2007-01-11
i don't know if it has anything to do with the inconsistent behavior of you card g0nzo but i've noticed something very strange when i setup an acx 100 or 110 chipset card (d-link) for my father. sometimes it connected all right, but most times it didn't, especially after reboot or removing and reinserting the card - the dhclient timed out trying to obtain an IP. the correct card driver was loaded properly but no IP...

resetting the connection with GUI network tools didn't help. finally i figured out a workaround: i needed to **manually** change the  /etc/network/interfaces file. touching the file had no effect, i had to change something and save the file, and then restart networks by executing 
```
sudo /etc/init.d/networking restart
```

i managed to write a script that changes the file and connects by a simple mouseclick but still it's all a mystery to me. i've read a lot of howtos and suggestions but nothing seems to explain what has been happening there. i'm posting this because i think it might help if you get connected once in a while - so your hardware is basically working - but connecting is unpredictable. however, i really don't understand the logic behind it, so i'm not sure if this procedure applies to you too. it's just a shot. 

but most of all i hope someone here can explain this :confused:

---

### Post by g0nzo on 2007-01-15
@PatrickMay16:

In Kubuntu 6.10 it worked very well. I was downloading lots of upgrades and most of the time it worked at the maximum speed (~150Kb/s). I'm not sure how it works in LAN, didn't try it.

Using Ubuntu 6.10 live CD I managed to configure wifi connection without any problems.

I need to reinstall linux (not sure if Ubuntu or Kubuntu) and if I have time, I'll try to test LAN connection speed.

---

