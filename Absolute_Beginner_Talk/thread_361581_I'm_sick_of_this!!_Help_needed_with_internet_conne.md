---
title: "I'm sick of this!! Help needed with internet connection"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-14
Every time I connect to the internet, the connection lasts about 10 minutes if I am luck. It was like this in Dapper and now in Edgy, it sometimes closes after 2 minutes. My Network Connection says its just idle. What the hell is wrong!!!! AHAHAHAH
Thanks

---

### Post by banditti on 2007-02-14
What do you mean?  The connection dies or firefox shuts down or?  What do you have to do to get it back?  Can you be more specific?

---

### Post by ayed on 2007-02-14
Uh, for instance if I am downloading a file from the internet say from a torrent it connects and continue to download, but if while opening the firefox it says it cannot find the server. Even after the download is over its still cannot open anyhting. If gaim is connected it stays connected for a long time, and if like after 10 minutes idle when opening firefox it will say cannot find server but gaim is still connected and I can chat. To fix it I type:
poff dsl-provider
then 
pon dsl-provider
then it works?

---

### Post by justin whitaker on 2007-02-14
> **ayed said:**
> Uh, for instance if I am downloading a file from the internet say from a torrent it connects and continue to download, but if while opening the firefox it says it cannot find the server. Even after the download is over its still cannot open anyhting. If gaim is connected it stays connected for a long time, and if like after 10 minutes idle when opening firefox it will say cannot find server but gaim is still connected and I can chat. To fix it I type:
poff dsl-provider
then 
pon dsl-provider
then it works?

I don't think that has anything to do with Ubuntu. It's probably a modem issue, or something going on with your provider.

---

### Post by ayed on 2007-02-14
On my parents computer, XP, its stays connectes. I'm telling you that it continues to stay connected when downloading an file, but firefox cannot connect to the server?

---

### Post by Jussi01 on 2007-02-14
Try installing epiphany browser (its in the repos) - run that for a while and see if things are better.

---

### Post by ayed on 2007-02-14
Ok, did like u told me...installed the epiphnay...same result ;(
AHAHAHAHAH

---

### Post by banditti on 2007-02-14
Do you lose your ip stack?  can you ping the router?  Past the router?  When it is working can you ping yahoo.com and get the ip address.  Then, when it is not working, can you ping by IP?  

Trying to see if it is an IP stack or maybe a DNS issue.


Also, can you post your /etc/network/interfaces ?

---

### Post by Maestro23 on 2007-02-14
> **banditti said:**
> Do you lose your ip stack?  can you ping the router?  Past the router?  When it is working can you ping yahoo.com and get the ip address.  Then, when it is not working, can you ping by IP?  

Trying to see if it is an IP stack or maybe a DNS issue.

Just to piggyback on Banditti, can you run a traceroute back to your ISP?

If you don't have that command installed.

sudo apt-get install traceroute

Then in a terminal:

traceroute (your ISP address).

Might can see where it is having trouble at along the route.

---

### Post by justin whitaker on 2007-02-14
> **ayed said:**
> On my parents computer, XP, its stays connectes. I'm telling you that it continues to stay connected when downloading an file, but firefox cannot connect to the server?

Exactly how are you connecting? Via a router? 

My setup is:

Verizon ADSL>>>>>modem>>>>router>>>Ubuntu>>>>XP Laptop (Wife's)

I am logging in on both systems, and when they fail, it is usually the modem that is the issue, particularly after a long bout of downloading. 

I unplug the modem and the router, powering it down, and plug it back in. 

Try that.

---

### Post by banditti on 2007-02-14
Found this, it looks like it has fixed other peoples similar issues:

```
http://www.ubuntuforums.org/showthread.php?t=186430
```

---

### Post by spamzilla on 2007-02-14
I don't know if this will help, but here's an idea:

Go to System > Admin.. > Networking > Select DNS tab > enter the Open DNS server Ip addresses on seperate lines:

208.67.222.222
208.67.220.220

Close the program > open terminal > restart network:

sudo /etc/init.d/networking restart

and hope this works. If it doesn't I have one more trick which may help, but I'll post that if things don't go well.

Good luck :)

---

### Post by ayed on 2007-02-14
Spamzilla, what the hell did you do man! Its workin!! I owe you big time. Can I ask you what you did? Sorry for bothering the rest!
Thanks
Loooove Ubuntu!!

---

### Post by ayed on 2007-02-14
Flase alarm, it didnt last for long. Whats the other trick you had up your sleeve?

---

### Post by banditti on 2007-02-14
can you report on the couple of posts I asked about?

---

### Post by spamzilla on 2007-02-15
> **ayed said:**
> Flase alarm, it didnt last for long. Whats the other trick you had up your sleeve?

Again, Im not sure if this will help, but it got my internet up and running:

Open Terminal and backup the dhcp3/dhclient.conf file first:

sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak

2. Edit the dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

3. Look for the following line:

#prepend domain-name-servers 127.0.0.1;

Remove the comment (#) and change it to the ip address of your dns servers:
example:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

4. Restart your network

sudo/etc/init.d/networking restart

Now try to connect to the net. If it doesn't work, try this:

Turn off ipv6 via your browser:

Open web browser > in address bar type

about:config

In the filter bar type

ipv6

Double click the entry so the value is set to true.

Restart browser and hope for best.

Good luck, but the issue may well be with your equipment.

---

### Post by Wim Sturkenboom on 2007-02-15
No solution for the problem, but a possible explanation how it fails.

A program like gaim is either configured with an IP address or it looks up a hostname and gets the IP address. After that, it will use the address and lookup is no longer required.
Same for other apps.

However, each time that you go to a page with the browser, it will do a lookup. If the DNS fails, it can not translate the hostname to IP address and that's why you get the 'server not found' message'.

I suggest following spamzilla's suggestions.

---

### Post by ayed on 2007-02-15
I did like you told me spamzilla, except I didn't need to do the iPV6 thing. And I am connected, all I have to do now is wait a while and see if it disconnects. Thanks anyways.

---

### Post by ayed on 2007-02-15
I also did a traceroute, here it is:
ayed@ayed-desktop:~$ traceroute 196.27.0.29
traceroute to 196.27.0.29 (196.27.0.29), 30 hops max, 40 byte packets
 1  194.165.130.224 (194.165.130.224)  73.879 ms  71.803 ms  75.811 ms
 2  194.165.130.1 (194.165.130.1)  72.161 ms  75.735 ms  71.906 ms
 3  194.165.130.19 (194.165.130.19)  78.283 ms  71.876 ms  76.069 ms
 4  *
 *
 *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *

---

### Post by ayed on 2007-02-15
Guys, I'm sorry for dragging on like this...It didn't work. I guess I am doomed to redial eery ten minutes.
Thanks Anyways...You Guys Rock 
Ayed

---

### Post by ayed on 2007-02-15
> **banditti said:**
> Found this, it looks like it has fixed other peoples similar issues:

```
http://www.ubuntuforums.org/showthread.php?t=186430
```

Further feedback to banditti, I tried the link you gave me...I couldn't even get connected...sorry!
:popcorn:

---

### Post by ayed on 2007-02-15
Uh, btw have ethernets, both have the same problem. One is Realtek, the second is VIA Technologies.

---

### Post by halfvolle melk on 2007-02-15
My guess is that your /etc/resolv.conf gets overwritten with each new lease. Check the output of **cat /etc/resolv.conf** when you have it working and check it again after it has stopped working. I had a similar issue and fixed by putting the nameserver in /etc/resolvconf/resolv.conf.d/head
Hope this helps.

---

### Post by HereInOz on 2007-02-15
Have you tried setting your Ubuntu machine with a fixed IP address in the same subnet as your router.  For instance, if the modem router has an IP address of 192.168.1.1 then go in to Networking and set the IP address of the Ubuntu machine as a static IP at something like 192.168.1.25 .  You will need to modify this according to the IP address of your router.

Then remove all the listed DNS servers, and enter the DNS server addresses provided to you by your ISP (you may have to ask them.

I am thinking that your router may be renewing the DHCP lease and causing the disconnection, and by setting a static IP, you remove that possibility.

Good luck.

---

### Post by adriantry on 2007-02-15
Hi Ayed

> **ayed said:**
> Every time I connect to the internet, the connection lasts about 10 minutes if I am luck. It was like this in Dapper and now in Edgy, it sometimes closes after 2 minutes. My Network Connection says its just idle. What the hell is wrong!!!! AHAHAHAH
Thanks

Which ISP are you with? Sounds similar to a problem a lot of people have with Bigpond.

Bigpond send a "heartbeat" (ping) every five minutes or so to see if you're still online. If they don't hear back from you, they disconnect. Firewalls and other network settings can block this heartbeat, meaning you get kicked off often.

If you feel this might be you're problem, there's a lot of information about it here:
[http://www.ozcableguy.com/heartbeat.html#intro](http://www.ozcableguy.com/heartbeat.html#intro)

Here's a quote:

"Telstra Cable uses an authentication system which has been nicknamed &#8220;the heartbeat&#8221; which is similar in concept to a &#8220;ping&#8221;. Every five minutes or so, a message is sent to your computer to see if you're still there.
Several applications like firewalls, Win98/ME ICS and VPNs block this message, causing the connection to drop out regularly."

I don't know whether this is you're problem. I hope you get it solved one way or another.

Adrian

---

