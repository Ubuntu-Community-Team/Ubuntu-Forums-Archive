---
title: "Internet connection gone"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by MadL on 2006-02-16
I've been running Ubuntu for about two weeks now, and I've been enjoying it...
But when I booted up tonight, I can't get onto the Internet. Both Firefox and Thunderbird just sit there, waiting for a response that never comes.

I also noticed this message during the startup menu:

> Synchronizing clock to ntp.ubuntulinux.org **[fail]**
Error: Temporary failure in name resolution

I was having some issues with my connection earlier, but it seems to work fine in Win2K now, and yet I still have this problem in Ubuntu. Suggestions?

**Edit:** BTW -- I'm using an Ethernet cable modem connection (Motorola SB5120), no router, if that helps.

---

### Post by TeeAhr1 on 2006-02-16
Just a hunch, but a name resolution error sounds like your DNS server/s are down.  (If you don't know what that is, it's a server maintained by your 'net provider that translates 263.22.0.3 into a [www.address.com](www.address.com) address.)  Why this hits you only in Ubuntu I have no idea, though.

Way to tell: When you try google.com or whatever, what's the status bar at the bottom of Firefox say?  If it hangs at "looking up google.com," you have a DNS problem.

This can be remedied by calling your internet provider's support (great fun, I know) and asking them for more DNS addresses.  Then go into System > Admin > Network, click on the DNS tab, click on Add, and plug them in.

---

### Post by rjwood on 2006-02-16
Before you call anyone check system>administration>networking.. 

Sometimes you need to reactivate your etho setting..

---

### Post by TeeAhr1 on 2006-02-16
Good advice, I should have thought of that.  Never eschew the simple stuff :)

---

### Post by MadL on 2006-02-16
I checked System > Administration > Networking, and it looked like eth0 was active. My ISP's website has a tool to check your connectivity, and it showed that all three DNS servers were unreachable. I even managed to get a *"that's weird..."* out of the ISP tech support person.

None of which explains why I still seem to be able to access the Internet using Win2K. I even put in my Knoppix 4.0 disc to see if there was a hiccup in Ubuntu, and I couldn't get on the Net using Knoppix, either.

If I were a bit more paranoid, I'd almost wonder if my ISP was trying to figure out a way to Linux-proof their service (good thing I'm not :) ).

---

### Post by MadL on 2006-02-18
Curiouser and curiouser...

It turns out that I'm technically connected to the Interent on Ubuntu, but the connection's just very, very s-l-o-w. If I wait long enough, I can get a website to appear after 5-10 minutes (sometimes), but Thunderbird times out when trying to get e-mail, and the clock synchronizations with ntp.ubuntulinux.org still says it can't resolve. Yet, Win2K is having no problem with the connection -- I can even get streaming audio and video. I've tried the solution offered in [this thread]("http://ubuntuforums.org/showthread.php?t=132385"), [this thread]("http://www.ubuntuforums.org/showpost.php?p=50664&postcount=2"), and [this thread]("http://ubuntuforums.org/showthread.php?t=131769"). No effect. Any thoughts?

---

### Post by patrick295767 on 2006-02-18
With Kcron /etc/crontab, u can run a script at a define time periodically to check if it's you Internet or router.
  and store that into a folder.
It's what I do & can then track when Internet is indeed gone or simply one cable... my investigation result is that my cable are always plugged but my Internet services not soo good and not so great ...
  
Greetings,

Patrick

---

### Post by kvorion on 2006-02-18
You did not mention what kind of connection is it that you have. I have been using rp-pppoe for a long time on linux (Fedora and Ubuntu), and I have faced this problem an awful lot of times (hell I still have it at times).

 Tell me if you are using a pppoe connection and I should be able to tell you about certain issues that cause this problem and things that you can try out. 

First thing. Connect to the internet the usual way you do. Type "ifconfig" on your teminal, and post the output here.

---

### Post by nalmeth on 2006-02-18
search the forums for ipv6 or something along those lines. I have heard it has debilitated some peoples net connections, and isn't typically needed, so is safe to disable

[http://ubuntuforums.org/showthread.php?t=132385&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=132385&highlight=ipv6)

heres a start

---

### Post by MadL on 2006-02-18
Aaand of course, now that I've been griping about it for a few days, up goes the connection again.

For now.

kvorion: I don't think I'm using a PPPoE connection -- I've got an Ethernet cable modem using a DHCP configuration (is that what you're asking about? Ubuntu automatically detected the NIC card and modem when I installed it, and I just went with the defaults. I'm still on shaky ground when it comes to Internet connection details).

When I ran ifconfig, here's what appeared:

> eth0      Link encap:Ethernet  HWaddr *(omitted)*
          inet addr:*(omitted)*  Bcast:*(omitted)*  Mask:255.255.252.0
          inet6 addr: *(omitted, but an address was listed)* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2106031 (2.0 MiB)  TX bytes:264318 (258.1 KiB)
          Interrupt:17 Base address:0xdc80

lo        Link encap:Local Loopback
          inet addr:*(omitted)*  Mask:255.0.0.0
          inet6 addr: *(omitted)* Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:481677 (470.3 KiB)  TX bytes:481677 (470.3 KiB)


---

### Post by kvorion on 2006-02-19
It does look fine now. What I was trying to find out is if you are able to login and if you are assigned an IP address by your DHCP server. But then you do say that your problem is solved atleast for the time being.

Tell me one more thing. What command do you use to connect?

something like "adsl-start" ?

---

### Post by MadL on 2006-02-19
The connection's already on when I log in; I don't have to enter a command. Is this something that would appear in the start-up menu?

Thanks to everyone for taking the time to help. The Ubuntu forums really are great!

---

