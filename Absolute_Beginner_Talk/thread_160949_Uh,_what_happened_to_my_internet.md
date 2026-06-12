---
title: "Uh, what happened to my internet?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-16
I just installed ubuntu to my other computer. First I ran the live cd to check how the hardware would work, and upon inserting the live cd, everything worked, (I have a dell 700m, intel PRO 2200bg wireless integrated) but on the live cd, as soon as it booted uip I was online and did not have to configure anything.  I just installed to my hard disk and the only icon i get in the upper right is the network status or what not, but no internet connection. why would it work on the live cd but not the install? what now?

---

### Post by unbuntu on 2006-04-16
Did you notice anything failed during startup?

---

### Post by dermotti on 2006-04-16
Run **ifconfig** and paste the results in here.

---

### Post by x5452 on 2006-04-16
i cant copy and paste because my computer that i need help on does not have internet :p  I ryan ifconfig, 
lo           link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr:   ::1/128  Scope:Host
             UP LOOPBACK RUNNING   MTU:16436   Metric:1
             Rx packets:  13590 errors:0 dropped:0 overruns:0 frame:0
             Tx packets: 13590 errors:0 dropped: 0 overruns:0 carrier:0
             collisions: 0 txqueuelen:0
             RX bytes: 1237195 (1.1 MiB)   Tx bytes:  1237195 (1.1 Mib)

sorry I tried to type it exactly as i saw it, hope this helps please...

---

### Post by Qrk on 2006-04-16
Also try 

```
sudo dhclient
```

If your network was detected by dhcp that may get it back, or at least spit out some interesting error messages.

---

### Post by unbuntu on 2006-04-16
[QUOTE=x5452]i cant copy and paste because my computer that i need help on does not have internet :p  I ryan ifconfig, 
lo           link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr:   ::1/128  Scope:Host
             UP LOOPBACK RUNNING   MTU:16436   Metric:1
             Rx packets:  13590 errors:0 dropped:0 overruns:0 frame:0
             Tx packets: 13590 errors:0 dropped: 0 overruns:0 carrier:0
             collisions: 0 txqueuelen:0
             RX bytes: 1237195 (1.1 MiB)   Tx bytes:  1237195 (1.1 Mib)

sorry I tried to type it exactly as i saw it, hope this helps please...[/QUOTE]


Only loopback interface is shown here.  Your network adapter isn't correctly set up by ubuntu for some reason...Like I said, did you notice something failed during startup?  If eth0 interface can't be detected, it will (normally) halt for a long time (during startup) before the red shiny text "failed" is spit out.  If so, you must have noticed.

---

### Post by x5452 on 2006-04-16
i did not notice anything fail durring setup. in fact it said it detected network hardware and asked me which to use, wireless 2200bg or another one, (ethernet landline i guess) i clicked to use the one it selected, my wireless card. it said configuring dhcp, it said success, then it booted up.

Edit: I ran dhclient, but it is way much to type in here, what am i looking for in that?.

---

### Post by Qrk on 2006-04-16
dhclient, if it worked, would actually connect you via dhcp. As for the error messages, I was only hoping I'd vaguely recongize them.

---

### Post by x5452 on 2006-04-16
ok now im utterly confused, i typed dhclient and it gave me information. when I read that it would connect me if it worked i tried, and now i am online and can go to web pages.  first off what did it do, why did that connect me? second, is it going to stay like that, where do i go to set that up as default if need be, ect...???

---

### Post by Qrk on 2006-04-16
dhclient is a way to automatically configure network hardware, from my (limited understanding) 

The nice thing about it is that if dhcp fails,  dhclient will try another network protocol. Because ubuntu didn't detect your network at boot, I assume dhcp failed. So trying another protocol would help... or if it didn't work, at least give some information. 

As for setting it as the default at boot up, I try not to mess with changing those settings. I've been burned several times. I can screw up X just fine, but I like to get a system that at least boots if I make a mistake. ;) 

I just made an icon on my panel that lauches dhclient and I click it whenever I loose my connection. Thats pretty sad, I know. I suppose it'd be easier to add dhclient to the list of commands to run when Gnome starts, but I sometimes loose my connection in the middle of a session, so I just keep my icon.

---

