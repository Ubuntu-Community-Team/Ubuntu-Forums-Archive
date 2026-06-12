---
title: "How do I control startup?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-12-30
I would like to choose at startup whether Internet is available or not. Can I do this in Grub? By default, I would like no Internet. How can I do this?

Thanks.

---

### Post by mikeb on 2005-12-30
Maybe my subject line is not good, but I would please like help with this question. I have read the Wiki, the Starters Guide and everything else I could find and nothing had the answer.

Thanks.

---

### Post by Rxke on 2005-12-30
You mean no connection to a network? Or set it up so you cannot connect to the 'net (for safety, assuming the computer is for 'other' people)

---

### Post by Rxke on 2005-12-30
Maybe this is what you are looking for?

[http://linux.softpedia.com/get/Internet/Proxy/squid-mysql-acl-8006.shtml](http://linux.softpedia.com/get/Internet/Proxy/squid-mysql-acl-8006.shtml)

Or a more general disable-network approach?

---

### Post by missmoondog on 2005-12-30
i would think the person is asking about controlling startup items. you know, items that load on start/boot? i would like to know also.

---

### Post by mikeb on 2005-12-30
OK thank you for the replies. What I am looking for is this way: I startup the computer (dual boot, using grub defaults to Ubuntu) without a network connection and it is fine because I have used BUM to disable TCP/IP. However, another time, I connect the ethernet cable and startup the computer, and this time I want to re-enable TCP/IP before the Ubuntu has started. Is this possible?

---

### Post by mikeb on 2005-12-31
Bump.

---

### Post by Rxke on 2005-12-31
I do not see the problem...
If you set it up for network connection, and unplug ethernet afterwards, that's not a problem... it doesn't 'break' anything...

---

### Post by mikeb on 2006-01-01
[QUOTE=Rxke]I do not see the problem...
If you set it up for network connection, and unplug ethernet afterwards, that's not a problem... it doesn't 'break' anything...[/QUOTE]

Thanks for the reply. Yes, I know about this. The problem is that I need to make it the other way: default is no Internet. The computer and my internet connection are separated by about 20m and one floor. The cable is loose and I run it down the stairs when I need it. If I could startup with Internet disabled (via BUM), then connect the cable and have Ubuntu discover it, that would be a solution, but, I don't think that would work, would it?

---

### Post by Rxke on 2006-01-01
ah! Ok, sorry, didn't quite get it... (reboots computer to see if setup works, just a minute)

---

### Post by Rxke on 2006-01-01
There we are again...

errr... For simple browsing, it works if you just install and configure your network stuff connected etc...

I rebooted with my ethernetcable unplugged, and only synchronising ntp timeserver failed. (duh)  Networks is set up, but it of course can't connect etc... 

Then I plugged  in the cable, and started Firefox and it connected just fine.

I work with connectionsettings w/o DHCP (fixed IP, through another (wireless laptop) computer that works as some kind of hub), maybe that could be the problem if it doesnt work with your setup? you can't get a DHCP setup?
you wrote: > I have used BUM to disable TCP/IP.  I still do not understand why, (but I'm a bit dense at times, esp. these days, heh) does it otherwise hang or so if you're not connected?

---

### Post by mikeb on 2006-01-01
[QUOTE=Rxke]
you wrote:  I still do not understand why, (but I'm a bit dense at times, esp. these days, heh) does it otherwise hang or so if you're not connected?[/QUOTE]

Well, I have just discovered I cannot disable Internet with BUM. But, yes, if computer starts up without connection it hangs and waits for several minutes. I use the computer only for playing music and movies. I have no need for Internet, so I would rather leave it unconnected, but then I have to wait for the boot-up since Ubuntu looks for the network connection.

---

### Post by d1337 on 2006-01-01
When it hangs at boot time, hit ctrl-c and it will skip that step.  I do this for network and synchronize clock on my laptop if I'm not on a wired connection.  It may seem like a pain, but after awhile, you just do it automatically.

d1337

---

### Post by mikeb on 2006-01-02
Thanks very much. I will try that.

---

### Post by mikeb on 2006-01-02
Thanks very much. I will try that.

---

