---
title: "Linksys Wireless G router non-wireless"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by nikolardo on 2008-03-10
i have read a number of forums on this and followed all directions i understood
this includes everything i understand at "192.168.1.1"
here's my deal:

i have a desktop computer running ubuntu.  i wish to connect my linksys wireless g router to it in a direct wired connection, not using a wireless card or anything
the only reason i want to do this is so that i can work wirelessly from my laptop
my laptop runs xp, but i'm not worried, i think i can make that connect well.  it's my desktop ubuntu feisty fawn that does not want to connect with a nice wired connection.

i have been to "192.168.1.1" and messed with setting there and followed various instructions, but i can not get anywhere
i would like a very detailed set of instructions for how to get my desktop computer to work with the router.
my internet is verizon dsl.
please help me out.

---

### Post by Rocket2DMn on 2008-03-10
On the router status page, can you see a public IP available?
Also, go to System->Administration->Network, select your wired connection, hit Properties and check Enable Roaming Mode.

---

### Post by nikolardo on 2008-03-14
well, i went into system > administration > network and enabled roaming mode as you said
but i'm finding that now i cannot actually get to "192.168.1.1"
firefox gives me the "cannot load page" thingy when i try to go there, and it still won't go anywhere else either.

---

### Post by Rocket2DMn on 2008-03-14
Can you please post the output of
```
ifconfig -a
```

---

### Post by nikolardo on 2008-03-14
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:18:1E:1E:6E  
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe1e:1e6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230355 errors:0 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47382242 (45.1 MiB)  TX bytes:283041816 (269.9 MiB)
          Interrupt:5 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17553 (17.1 KiB)  TX bytes:17553 (17.1 KiB)

---

### Post by Rocket2DMn on 2008-03-14
In firefox, type "about:config" into the address bar and search for "ipv6"
Change the value of "network.dns.disableIPv6" from "false" to "true"

Then run in a terminal:
```
gksudo gedit /etc/modprobe.d/aliases
```
and change the line
"alias net-pf-10 ipv6"
to
"alias net-pf-10 off"
Save and close.

Then reboot your computer, and maybe reset your router just for good measure.  After you reboot, can you access the 192.168.1.1 config page or websites?

---

### Post by nikolardo on 2008-03-15
i changed the ipv6 thing in about:cofig
and i did the stuff you said to with the code in gedit
and rebooted and reset the router
and i get nothing
no websites, no 192.168.1.1

---

### Post by ghost_ryder35 on 2008-03-15
> **nikolardo said:**
> i changed the ipv6 thing in about:cofig
and i did the stuff you said to with the code in gedit
and rebooted and reset the router
and i get nothing
no websites, no 192.168.1.1
have you tried doing a reset on the router (holding down the small button in the back with a pen or pencil for 60 seconds)

---

### Post by ugm6hr on 2008-03-15
> **nikolardo said:**
> this includes everything i understand at "192.168.1.1"


If you can access 192.168.1.1, then you are already connected to the router.

The issue is therefore either with the internet connection via the router (are you certain that the router is connected to the DSL modem, and the DSL modem has the correct verizon settings to get online), or with ipv6 (solution here: [http://ubuntuforums.org/showthread.php?p=2631546#post2631546](http://ubuntuforums.org/showthread.php?p=2631546#post2631546))

---

### Post by nikolardo on 2008-03-16
i have reset the router
when i first started trying to set this up, i could reach 192.168.1.1
i can no longer reach it or any websites when i am connected to the router
i have to directly connect to the dsl modem on my desk to get online
the modem works fine, but i want the router in between the modem and my dekstop so that i can use the wireless for my laptop
my desktop computer needs to be wired directly to the router, there's no reason not to, right?

---

### Post by ugm6hr on 2008-03-16
> **nikolardo said:**
> i have reset the router
when i first started trying to set this up, i could reach 
i can no longer reach it or any websites when i am connected to the router
i have to directly connect to the dsl modem on my desk to get online
the modem works fine, but i want the router in between the modem and my dekstop so that i can use the wireless for my laptop
my desktop computer needs to be wired directly to the router, there's no reason not to, right?

Bizarre that ifconfig gives a sensible DHCP ip address, but you can't access the router admin page.

Your best bet is to try and reverse whatever you did so far.  So turn roaming back off again.

As a start, connect the computer to the router with a cable, and turn both off.  Then turn the modem on, followed by the computer.

Then try accessing the admin page again 192.168.1.1

If that doesn't work, it might be worth connecting your laptop with a cable to the router to see if you can access the settings page from your laptop.

---

### Post by nikolardo on 2008-03-16
i was unaware that resetting the router took 60 seconds of holding the button
when i'd done it before, i'd just pressed the button and assumed it had reset
i did an actual reset and now i can reach 192.168.1.1
i'm not sure what to do now that i can get there, though, i've seen different sets of instructions saying different things

---

### Post by ugm6hr on 2008-03-16
Try this to start with:

[http://ubuntuforums.org/showpost.php?p=4522099&postcount=2](http://ubuntuforums.org/showpost.php?p=4522099&postcount=2)

PS: I am assuming you know how to connect the router to your modem.

---

### Post by nikolardo on 2008-03-23
everybody, thanks for you help, i got around the problem a different way.

---

