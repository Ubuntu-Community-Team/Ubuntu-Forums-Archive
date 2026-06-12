---
title: "Can connect to network - cannot connect to internet?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by rafarquhar on 2007-12-27
I just installed ubuntu (Gutsy) on a friend's machine.  I'm not sure what exact kind of ethernet card he has, but he has some linksys router.  I can connect to his router through firefox, but I cannot connect to the internet through firegox or pidgin.  The network is DHCP, and his DNS server is set up properly, the internet just seems to not work for no apparent reason.

Thanks for the help.

---

### Post by shearn89 on 2007-12-27
Make sure that he has an IP address from the router - run "ifconfig" in a terminal and check that eth0 has one.

Check proxy settings in firefox, and the global ones (not sure where this is - maybe in system -> administration?).

Check any firewalls aren't blocking stuff.

Thats all i can think of off the top of my head!

---

### Post by rafarquhar on 2007-12-27
Thanks for the suggestions, but none seemed to work.  The computer had an IP, and there were no issues with the proxies.  I also disabled all of the routers firewalls, but still no luck.
Any other suggestions?

---

### Post by djfick on 2007-12-27
can you ping the router from the pc?

when you try to connect to the internet, what error are you getting?

---

### Post by rafarquhar on 2007-12-27
It's connected, and I can ping the router from the PC.  When I attempt to go to a website, it just loads forever.

---

### Post by shearn89 on 2007-12-28
Can you ping [www.google.com?](www.google.com?) If so, have you tried another browser? something really simple like Kazehakase (or links?)
I had problems with my firefox being really really slow...

---

### Post by KentS on 2007-12-28
Try
```
ping -c 4 64.233.183.147
```

If this works, it might be a nameserver problem.

---

### Post by andlinux on 2007-12-28
You said that your dns settings were correct.
I'm connected here to the internet with a router and the standard gateway address is 192.168.1.1, I have that also set that as my dns address. 

You can try that to but with your ip address from your router.

---

### Post by NewbieNik on 2007-12-28
OK, lets do this one at a time.

Is the linksys router the gateway to the internmet (Ie a cable modem or ADSL modem)?
If so, access it through the web-interface and there should be a diagnostic page where you can ping from the router. Try pinging from that. If you get nothing then its possibly the router. May be worth rebooting it and the cable modem. (If its ADSL, have you got the microfilter plugged in?)
If that all works then it the connection from PC to router.
If you can see the router, but nothing external then check the GATEWAY address assigned by the router. It should be the routers address. If this is incorrect then your PC is talking to nothing and getting nowhere.
If that is correct and your ifconfig command gives you an IP address in the same range as the router ie 192.168.1.x (assumed you're on 192.168.1, most linksys routers are) then try pinging an external address rather than name. I don't have access to resolve IP addresses here so hopefully someone will pitch in.
If that works then its your DNS settings, but try the above and repost the results and we'll go from there. Also, give us some more details. Your IP, the routers IP any dns settings etc,etc,etc.

---

### Post by rafarquhar on 2007-12-28
Thank you guys very much for the replies.
I'll be heading over to his house later today hopefully to get it working, but here's what I know:

Shearn-
I can't ping google.

KentS-
I'm fairly certain that it wont work, since I couldn't ping any other addresses.  I'll try it today though.

andlinux-
I'll try it today, it sounds like it might work.  I think I might have already tried it though.

NewbieNik-
The linksys router is the gateway to the internet.  I'll try to ping from the router, though I think it's working, because his windows box was running from it.  I'll try what you said as well.  I'm pretty sure that his network IP was 192.168.1.100, but that's just how his router is set up for some reason.  The router's ip was 192.168.1.1, and the DNS server was set to something else, which I'll check again when I stop by today.  I'm also noting how my router is setup, as I'm sure his is similar.

Thanks for all the help guys, and sorry for the lack of info I'm providing.

---

### Post by KentS on 2007-12-28
rafarquhar, andlinux and my own suggestion is essentially the same. 64.233.183.147 is the ip address belonging to the hostname [www.google.com](www.google.com). You're browser uses DNS/nameservers to translate between ip addresses and hostnames. If you can ping 64.233.183.147, but not [www.google.com](www.google.com), that means your DNS/nameserver settings are wrong. One possible fix to this is to add
> nameserver 192.168.1.1
to your /etc/resolv.conf (if the LAN address of your router is 192.168.1.1)

---

### Post by LPA on 2007-12-31
I have an almost identical problem. Old Pentium 3 with Ubuntu 7.10 freshly installed (I've installed and reinstalled in vain attempts to solve this problem, both with a downloaded version and an original version CD).
Install goes perfect - no error messages. Everything works, EXCEPT I cannot access the internet. Access is through a cable to a router (wireless and wired), which has 2-3 other WINDOWS computers working through it - all work perfect. 
Have 'pinged' sites, so I know the cable and the network card work fine, but it refuses to access the net.
Any and all suggestions will be gratefully accepted!
Richard

---

### Post by LPA on 2007-12-31
PS to my previous post - please reply also to my direct email address: [email]richard@LPAgroup.biz[/email]

many thanks

---

### Post by jaya9w2bug on 2008-01-03
Haa.... I had the same problem. It's with the ipv6 protocol which enabled by default. Keyword is "disable ipv6" on the help menu. Take a look. Hopefully it will solve your problem.....Have a nice day

---

### Post by noobsyd on 2008-04-08
Hi - I had the same problem.

I connect through a Netcomm V300 VOIP router - VOIP worked fine; XP could connect to the www OK but Ubuntu could not.

Anyways - I followed the solution below and is working just fine now.

Cheers!

[http://ubuntuforums.org/showthread.php?t=539717&highlight=v300]("http://ubuntuforums.org/showthread.php?t=539717&highlight=v300")

---

### Post by bumanie on 2008-04-08
The only way I could connect with gutsy was by disabling ipv6 in firefox
Open firefox, in the address bar type about:config. In the filter type ipv6. On the line that appears right click and then left click on toggle to change the value to true. If that doesn't work you can reverse it by changing toggle back false by going through the same process. Hope it works.

---

