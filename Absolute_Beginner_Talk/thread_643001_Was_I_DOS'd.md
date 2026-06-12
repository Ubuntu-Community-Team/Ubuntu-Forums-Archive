---
title: "Was I DOS'd?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by rustyisle on 2007-12-17
Last night a server I help manage (not Ubuntu based) was working just fine.  This morning, it was not responding to SSH, HTTP, FTP, or anything else, but it was responding to pings. In addition, I had an open connection to the box from last night and that WAS still active.

I was forced to have the server rebooted on site before I could ssh back into the box.  Once I got in, I took a look at the /etc/var/message log and saw that the log was recording at Dec 16 @ 8pm, and then the next entry is Dec 17 @ 10am (when the server was rebooted).  Oddly enough, I know people were using the server for multiplayer games past 830pm.

I examined the messages log more and saw one IP address which attempted to login to the computer 7368 times under various attempts (ssh, http, etc).

From this, I'm guessing someone tried to login so many times that they hammered our servers connections and overflowed it or what not.  A reboot cleared it all up and we can connect again.

My question: Am I barking up the wrong tree or am I on the right track?  Besides blocking these ips in hosts.deny, are there other things I can do?  I was contemplating having SSH restart automatically via a cron job each night.

Suggestions?
Much appreciated.

---

### Post by Tom Mann on 2007-12-17
It doesn't sound great whatever happened, however even with a number like that these things can happen innocently (like a bug in a program).

The best thing to do is block the IP from your firewall rather than the server itself. (Or see if your ISP can block it - the further down the line the better)

---

### Post by jaybombalous on 2007-12-17
who has the server? how is it setup, behind a router? Some not so great routers can crash under heavy load of connections. U said he tried ~8k times. depending on how many of those connections never closed could the be the reason for the lockup, but u said the server was operating past 8:00 pm when the log stopped How may of those people where already connected and how many people could connect after that time?

I say this because an open connection that is active still may work even though all connections from that point on will be refused. 

Also, I would put a lock on the account to login with, sounds like he brute forced it. if thats the case then lock the account after 3 failed tries until another 24 hours has passed.

with the 24 hour lock out, he will either get discouraged or he will keep trying and give u more time to track his *** down.

---

### Post by lespaul_rentals on 2007-12-17
Sounds like it wasn't DDoSed,  rather bruteforced.  Block those IPs, but don't trust a simple block to protect you, as he was probably using a proxy.  Get some software or a filewall to limit the number of failed logins to 5 or so.

---

### Post by jba6511 on 2007-12-17
I would look into getting an IDS to monitor connections to the server. Snort is an excellent open source one and there are guides on the forums for installing it. Often, they will perform port scans and do other various reconnaissance of your network before trying to exploit services. Snort will let you see this activity and set up email alerts to notify you.  While not a direct solution to the problem, it will help you to identify when an attack may be coming.

---

### Post by rustyisle on 2007-12-17
Thanks for the tips.  So far I've manually added the stuff into hosts.deny to at least do something.

I'll look today for some software to do some of this automatically.  Any suggestions?

Thanks again.

---

