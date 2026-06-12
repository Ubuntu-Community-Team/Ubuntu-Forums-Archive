---
title: "My X-friend and Verizon DSL-need help"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-21
I was happily cruising along here for the past 3+ months until an ex-friend, in another forum, suggested that I run;

> sudo pppoeconf

After doing so and following his instructions I got this; "Access Denied" from Verizon. I'm now unhappily writing this in IE. 

Question is: How do I reverse what the above sudo did or how to get back on line with Verizon by another means?

I'm not very conversant with all the commands as yet so _Please_ be explicit in any replies.

Many thanks,

Jon

---

### Post by vtel57 on 2007-05-21
In your Gnome Main Menu --> System --> Administration --> Network:

Give your password. When the Network window opens, you should see an item (eth0) in the window under the Devices tab. Double click on it. Another window will open. In that window, about half way down, you'll see "Automatically obtain IP address settings with --> a drop down menu. Click on the drop down list and choose DHCP. Now, below that, you'll see DHCP Settings. Make sure "Automatically obtain DNS information from provider" is checked. Accept/Save those settings. Reboot you machine and see if you now have I-net access.

Luck!

---

### Post by Romin-1 on 2007-05-21
Hi vtel57, thanks for the reply;

Did as you suggested. DHCP was selecred but there was no checkbox for "Automatically obtain DNS information from provider" in there any where.
Rebooted with no joy. "Access Denied"

I have the Verizon software on a cd but I don't think it will work in Dapper Drake.

Any other ideas? i hope,,,

Yours,

Jon

---

### Post by vtel57 on 2007-05-21
A note to the wise: You will **never** need that Verizon crap software to get online with any operating system. ;)

Open your Terminal program and enter this command:

```
 $ ifconfig
```

Please post the output of that command here.

---

### Post by Romin-1 on 2007-05-21
Here ya go, vtel57:

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:AD:7D:FB:76
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe7d:fb76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2344291 (2.2 MiB)  TX bytes:443343 (432.9 KiB)
          Interrupt:3 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2366 (2.3 KiB)  TX bytes:2366 (2.3 KiB)

Hope it makes more sense to you than it does me.

Jon

---

### Post by vtel57 on 2007-05-21
Hi Jon,

We're going to try something here. In your Terminal, type this command:

```
 $ ping -c3 www.google.com
```

Please post the output here. It may look something like this:

```
[vtel57@ericsbane03 ~]$ ping -c3 www.google.com
PING www.l.google.com (209.85.165.99) 56(84) bytes of data.
64 bytes from eo-in-f99.google.com (209.85.165.99): icmp_seq=1 ttl=242 time=38.0 ms
64 bytes from eo-in-f99.google.com (209.85.165.99): icmp_seq=2 ttl=242 time=37.6 ms
64 bytes from eo-in-f99.google.com (209.85.165.99): icmp_seq=3 ttl=242 time=38.7 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 37.604/38.112/38.716/0.485 ms

```

---

### Post by Romin-1 on 2007-05-21
Well vtel57 after I made the last post I tried the sudo thing again and this time I said NO to one of the things there and re-booted and now the danged thang is working.

Below is the output for the ping in case you still want to take a look.

~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=243 time=35.5 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=243 time=34.8 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=243 time=34.4 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2009ms
rtt min/avg/max/mdev = 34.446/34.940/35.518/0.491 ms

At this point I'm a little leary of shutting the pc down or even going to XP for something. Guess I'm afraid my fix won't hold.

Jon

---

### Post by vtel57 on 2007-05-21
Ooops. That was my error, Jon. I should have told you to reboot after adjusting the DHCP settings. Mea culpa! Anyway, as you can see from your ping output, you are indeed online.

E[COLOR="Red"]DIT: Oh, wait. I did remember to tell you to reboot. Hmm... maybe you didn't pick up the local DNS server the first time you rebooted. Well, anyway, I think you should be OK now. No more playing with PPPoe, OK?[/COLOR] ;)

For your information, if you don't know what ping is, it's sort of like a submarine sending out a sonar ping. You're actually sending a series of packets, three in this case (-c3), to the [www.google.com](www.google.com) server. Their server receives the packets and then confirms receipt. Ping is a handy tool. I usually ping google because I know their servers are ALWAYS up and running.

You fixed it, I'm pretty sure. :)

Have FUN! 

~Eric

---

### Post by wellsuser on 2007-05-22
Since it seems that getting online via a verizon dsl connection is a common challenge for noobies like me, I'm spelling out what I did, after reading the Romin-1/vtel57 exchange. FYI, I am using the old-fashioned command-line approach, not one of the GUI interfaces. And the msgs below are paraphrases, not verbatim.

1. At a command-line prompt, typed sudo pppoeconf.

2. Program searches for networking devices and asks if it has found all of them (Y/N). I typed Y.

3. "If you continue, the config file /etc/ppp/peers/dsl-provider will be modified. (Y/)." I typed Y.

4. "Most people with popular dialup connections prefer the options 'noauth' and 'defaultroute' in their configuration file, and remove the 'nodetach' option. Should I check and change? (Y/N)." I had no idea what this meant, but I figured verizon dsl has to be one of the most "popular" connections, so I typed Y.

5. "Please enter the username for the ppp login." This is your verizon-assigned user name.

6. "Please enter the password for the ppp login." This is your verizon account password.

7. "You need at least one DNS IP address to resolve the normal host names. Normally your provider sends you addresses of useable services whenthe connection is established. Would you like to add these addresses automatically to the list of nameservers in your local /etc/resolv.config file? (recommended) (Y/N)" Again, I'm not really sure what this means, but typed Y, since it was recommended.

8. Some long message about "Limited MSS Problem." Really didn't understand this, but typed Y.

9. "Now you can make a DSL connection with 'pon dsl-provider' and terminate it with 'poff.' Start a connection now? (Y/N)."  Typed Y.

10. "The dsl connection has been triggered. You can use the 'plog' command to see the status or 'ifconfig ppp0' for general interface info. Entered the latter command, and saw some stats that indicated I was online.

11. Tested the connection with 'ping www.google.com."  Got repeated stream of replies from the google site, indicating I was indeed online. (Broke the ping loop with Ctrl-c. On some systems, it's Del.)

That's the saga. Haven't yet done anything useful with the connection. But, at least I'm on -- and hope this solves your problem, too.

---

### Post by vtel57 on 2007-05-22
You done good! That's the wonderful thing about GNU/Linux...  there are more ways than one to solve problems. The main reason I had Romin do this in the GUI is because this is the Absolute Beginner area, and most beginners with GNU/Linux freak out when you say "command line". ;)

---

