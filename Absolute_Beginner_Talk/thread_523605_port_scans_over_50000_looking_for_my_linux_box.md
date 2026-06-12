---
title: "port scans over 50000 looking for my linux box?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ubunuby on 2007-08-12
I'm using ADSL with  PPPoE so I've got a pool of IPs which I was hoping to provide some obscurity based security, but one thing I've started paying attention to is that I'm getting hits on my firewall from machines looking for ports in the high 49,000 to low 50,000 range. I dont know if this is typical or not, but aren't these port ranges that linux uses for outbound connections (32769 and up)? 

I've had a major problem with an obsessive hacker,  and I recently switched to Ubuntu so I could feel better about using only trusted files, but is it at all possible my entire IP pool is being scanned on these high ports looking for my linux box specifically?  When I used to run my unknowingly hacked windows, I saw port scans between 1028-1032 which I know are the first open ports windows uses. 

The scans come from **many** different IPs, and happen on nearly any IP I obtain from the pool, but they are semi-infrequent only happening a few times in the range of several hours. 

I dont have **any** listening ports or services,  and no wireless connections either. Any idea whats going on here, and if it's intrusion related, what type of attack might he be trying?

---

### Post by heimo on 2007-08-12
My guess. Probably p2p traffic trying to connect to computer that earlier had same ip address.

---

### Post by ubunuby on 2007-08-12
I've seen that happen with bittorrent before, but I recognize that port. What kind of p2p uses these kind of port numbers and how could nearly every IP in my pool be doing it?

---

### Post by Warren Watts on 2007-08-12
I'm afraid I don't have an answer to your questions, but I do suggest you tighten your security if you already haven't.  It's good you don't have any listening ports, my advice is to install Firestarter and block everything.

---

### Post by heimo on 2007-08-12
> **ubunuby said:**
> What kind of p2p uses these kind of port numbers and how could nearly every IP in my pool be doing it?

Many clients randomize ports to bypass ISP filtering (and use high ports). Of all internet traffic, large portion is p2p traffic.

---

### Post by ubunuby on 2007-08-12
I know how to run a sniffer, but I haven't the slightest idea how to interpret the data, could you tell me anything to look for in the capture data that would clearly define the packets as P2P traffic?

---

### Post by heimo on 2007-08-12
> **ubunuby said:**
> I know how to run a sniffer, but I haven't the slightest idea how to interpret the data, could you tell me anything to look for in the capture data that would clearly define the packets as P2P traffic?

Well, there's no connection established, right? Then there will only be first part of tcp handshake and your system rejects or denies connection. It's probably pretty much undistinguishable from any other traffic (until connection is established).

---

### Post by bwtranch on 2007-08-12
Geez, I 've never had any problems quite that bad. Even when I had windows with limewire. Although it did bring a lot of malware in, I was still able to filter most of it out. Well, ok, you should shut down port 8080 that might kill bittorrent if you use that. Personally, I hate it. But, you can set your bits to use a different port.  But, I do think that bittorrent is the greatest security risk on a Linux machine and bar none.

I really can't think of anything else. 'cept for my old lady, she's a big security risk. Ha

---

### Post by ubunuby on 2007-08-12
You say even while running a p2p client you wouldn't get this many scans on odd ports? Then there is cause for concern? 

I don't run any services, so I'm not worried if this is genuinely p2p traffic, I'm more worried about accurately identifying it and knowing why its so prevalent, When I get an IP that was just using Bittorrent I get slammed on the standard port by a few dozen sources. I know nothing about intrusions or scanning, but could this be a large slow scan of my IP pool?  

Is there any other way of positively Identifying this traffic? or What to look for if it is some type of scan?

---

### Post by skymera on 2007-08-12
i used have a lot of blocked IP;s
ranging from port 22 to over 50000

sometimes it would be like 200 in an hour.
thisonly happened when i forwarded a few ports on my router.

but i see you are wired..hmmmm

---

### Post by skymera on 2007-08-12
try whois <ip>

that tells you sopme information on that address..

mine were all microsoft and hotmail abuse lol

---

### Post by ubunuby on 2007-08-12
**OMG** Why didn't I think of this!

I reinstalled, so I don't have my logs anymore but the ones I got in the past few hours are from Yahoo and voice yahoo...

Thanks for the tip I'll keep checking.

---

### Post by ubunuby on 2007-08-12
Just now I suddenly got hit by several dozen different machines over a few minutes from various user IP's euro and US. 

I'm guessing they are bots, and the port was 44587, someone in another thread mentioned a "flooder" any ideas whats going on here or how I can double check all is ok?

---

### Post by heimo on 2007-08-12
> **ubunuby said:**
> I'm guessing they are bots, and the port was 44587, someone in another thread mentioned a "flooder" any ideas whats going on here?

[http://www.f-secure.com/v-descs/flooder.shtml](http://www.f-secure.com/v-descs/flooder.shtml)

For current trends, see:
[http://www.dshield.org/indexd.html](http://www.dshield.org/indexd.html)

---

### Post by ubunuby on 2007-08-12
so this is somewhat normal and I shouldn't panic since I know I  couldn't possibly have a trojan on that port?

---

### Post by steve.horsley on 2007-08-12
My advice is to ignore it. You are unlikely to figure out what attack would have followed had an open port been found, unless you deliberately open a port and watch. It sould be scans looking for a weakness to attack, could be innocent misconfigured p-p connections, could be bots loooking for other compromised machines (friends or competitors), you don't know.

Forget security by obscurity. You are in a position to understand now why that's not safe.

Use your firewall to only allow trusted hosts to connect to the services you offer. Use secure communications, SSH, OpenVPN etc. depending on your applications requirements.

---

### Post by wirelessmonkey on 2007-08-21
Methinks this be World of Warcraft torrent update traffic.

---

