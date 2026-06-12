---
title: "Help with server."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by PooingCavy on 2008-03-01
Ok, sorry, im using Fedora 8, lol, and I don't feel like switching back to Ubuntu.

Anyways, the server ive set up is my mom's computer.

I can connect via 192.168.0.3

I cannot connect via the "external" or "public" (I dunno the name) IP, like how you can use that instead of the domain because the domain is some weird DNS redirect shizzle.

So, anyways, how do I get it so when using the external IP, I can connect?

I am on a D-LINK DIR615 router. I read a review on it, and it will let me put a webserver shizzle on it.

Also, the router is 192.168.0.1


kthxbai

---

### Post by Oldsoldier2003 on 2008-03-01
> **PooingCavy said:**
> Ok, sorry, im using Fedora 8, lol, and I don't feel like switching back to Ubuntu.

Anyways, the server ive set up is my mom's computer.

I can connect via 192.168.0.3

I cannot connect via the "external" or "public" (I dunno the name) IP, like how you can use that instead of the domain because the domain is some weird DNS redirect shizzle.

So, anyways, how do I get it so when using the external IP, I can connect?

I am on a D-LINK DIR615 router. I read a review on it, and it will let me put a webserver shizzle on it.

Also, the router is 192.168.0.1


kthxbai

Without going into the schizzles and 1337speak, clearly stating the problem tends to give better results. The reason you can't connect using the external ip is most likely that you are not port forwarding through your router to the server.

---

### Post by PooingCavy on 2008-03-01
ive tried to forward the ports 8- and 21 and whatever else I needed to 192.168.0.3

it still doesnt work.

---

### Post by Nythain on 2008-03-01
what type of "server" are we talking about here, what/how are you attempting to connect... i mean, are we talking samba, ssh, http, irc, telnet, ftp...

the term "server" is for shizzle not very descriptive here

---

### Post by pommattski on 2008-03-01
I'm assuming it's a web-server that you've set up on a PC at 192.168.0.3 which you want to be able to access from outside your LAN...
In your router, you should forward Port 80(TCP) to 192.168.0.3

This may be dependent on the router you are using, but you *may* not be able to access your server by browsing to your external IP address on a PC on the same LAN.
I have a web-server on my local LAN which I can access by browsing to it's local/private IP, but not my connections external IP - however, I can access it from an external location.

Matt

---

### Post by Nythain on 2008-03-01
not sure what isp you use also, but some (granted not as many any more) go as far as to block incoming port 80 connections to customers ip's... some isp's just dont want you runnin servers if you're not paying them for it :(

probably not the problem in your case, but it is a very rare possibility

---

### Post by PooingCavy on 2008-03-01
> **pommattski said:**
> I'm assuming it's a web-server that you've set up on a PC at 192.168.0.3 which you want to be able to access from outside your LAN...
In your router, you should forward Port 80(TCP) to 192.168.0.3

This may be dependent on the router you are using, but you *may* not be able to access your server by browsing to your external IP address on a PC on the same LAN.
I have a web-server on my local LAN which I can access by browsing to it's local/private IP, but not my connections external IP - however, I can access it from an external location.

Matt
Bingo.

I do have it port forwarded, I am not sure if I did it right. Ill give a snapshot.

[IMG]http://img148.imageshack.us/img148/7214/screenshotdlinksystemsisc0.png[/IMG]

---

### Post by Nythain on 2008-03-01
yeah, that theoretically looks right...

so my next question/suggestion would be... drum roll please... is the server running any sort of firewall???

---

### Post by pommattski on 2008-03-01
That looks to be correct, but maybe someone familiar with DLink routers can confirm this. Sometimes other settings can have an effect also.

---

### Post by PooingCavy on 2008-03-01
[IMG]http://img212.imageshack.us/img212/2649/screenshotdlinksystemsiic8.png[/IMG]

EDIT: This is new:

401 Unauthorized
Authorization required.

---

### Post by pommattski on 2008-03-01
Have you tried asking someone outside your lan to browse to you external IP?

---

### Post by igknighted on 2008-03-01
Stupid question... but are you using your external IP and not the 192.X.X.X address to try to connect from outside your network?

---

### Post by PooingCavy on 2008-03-01
lol.

MY 192.168.0.3 address works.

I am almost certain I am using the correct IP

[http://70.114.16.188/](http://70.114.16.188/)

I got it from the wat is my ip site.

---

### Post by Nythain on 2008-03-01
thats a step in the right direction i guess... unauthorized is better than no connection at all...
**401 Unauthorized**

     The request requires user authentication. The response MUST include a    WWW-Authenticate header field  containing a challenge    applicable to the requested resource. The client MAY repeat the    request with a suitable Authorization header field. If    the request already included Authorization credentials, then the 401    response indicates that authorization has been refused for those    credentials. If the 401 response contains the same challenge as the    prior response, and the user agent has already attempted    authentication at least once, then the user SHOULD be presented the    entity that was given in the response, since that entity might    include relevant diagnostic information.

so, not sure how that really applies to your scenario, because i dont know what your apache2.conf looks like, and or what the site's code looks like, oh yeah, and im not really a web design guru :(

but i look at this error as advancement, because at least now you are getting a connection

---

### Post by PooingCavy on 2008-03-01
Is anyone else getting the unauthorized messege?

Id like to know, ive gotten it only once, and now it seems its going back to the "lulz no connection"

---

### Post by Nythain on 2008-03-01
im seriously almost curious if fedora (i believe thats what you said you are running) isnt running a firewall or some sorts...

the server is technically there, but i've been waiting for a reply from it for a few minutes now :(

EDIT: and after many minutes stuck waiting for XX.XX.XX.XX i get a "Bad Response From Server"

---

### Post by Oldsoldier2003 on 2008-03-01
> **Nythain said:**
> im seriously almost curious if fedora (i believe thats what you said you are running) isnt running a firewall or some sorts...

the server is technically there, but i've been waiting for a reply from it for a few minutes now :(

EDIT: and after many minutes stuck waiting for XX.XX.XX.XX i get a "Bad Response From Server"
another possibility is he has the router configured for remote administaration which would mean that http requests would land people on the router admin page. not an optimal situation...

---

### Post by PooingCavy on 2008-03-01
Correct, fedora.

I followed the howtoforge guide. I believe it had disabled the firewall.

edit: It was enabled, I disabled it.

I wonder just how bad I am exposing my computer to hackers... lol.

edit2: wow, the firewall is disabled (on fedora), but it is still not connecting.

About the admin thingy.

I had my firefox windows tabs so it had the router and the 70.114.whatever, and I got the prompt for the router. I dunno if it was associated with the router or the 70.whatever

---

### Post by PooingCavy on 2008-03-01
Didn't feel like editing, since you guys prolly already had a response.

Anyways, ill reenable the firewall for safety.

edit: Remote management has been disabled, and is staying disabled. Thanks for the heads up.

---

### Post by Nythain on 2008-03-01
still not having any luck on my end :( and minus firewall, virtual server/port forwarding/remote management... i really dont know whats left to be getting in the way of the connection

ps... unless you're actually running an ftp server on that machine also, you really dont need to be forwarding port 21

---

### Post by PooingCavy on 2008-03-01
By FTP connection, I want to (this is stupid), I am kind of lazy and don't feel like moving my flash drive physically, so I wanna just use FTP.

Do I need that though if its within the local network? or do I get rid of that port opening?

FTP is blocked at school, and I really only touch my stuff from home.

---

### Post by Nythain on 2008-03-01
i wouldnt use ftp for anything within the lan... then again, i wouldnt use ftp for anything period... i've grown to love ssh and spc/WinSPC... ftp servers arent very practical for personal usage, complicated to set up, vulnerable, etc...

then again, for local area connections, im also a big samba/nfs fan :)

---

### Post by PooingCavy on 2008-03-01
*waits for some super-expert at this stuff*

---

### Post by PooingCavy on 2008-03-01
Hello?

---

### Post by PooingCavy on 2008-03-02
Are you still there?

---

### Post by Oldsoldier2003 on 2008-03-02
> **PooingCavy said:**
> By FTP connection, I want to (this is stupid), I am kind of lazy and don't feel like moving my flash drive physically, so I wanna just use FTP.

Do I need that though if its within the local network? or do I get rid of that port opening?

FTP is blocked at school, and I really only touch my stuff from home.
use ssh and sftp protocol or ssh and scp.  Filezilla is  a nice gui client and is available in windows and linux builds

---

### Post by PooingCavy on 2008-03-02
Ill just use a flash drive.

I have a 1gb, a 512mb, and a 256mb.

---

### Post by PooingCavy on 2008-03-02
Any ideas on how to get it to work?

---

### Post by PooingCavy on 2008-03-10
Well, it turns out that Roadrunner has done it again.

They have disappointed me with the blocking of port 80, and that they don't want servers on their network.

Ill try to convice my dad to look at other options.

I am really unsatified with Time Warner Cable. I mean, the internet is slow, the CNN randomly drops, there is no discovery channel HD (Theres HD theatre, but no Mythbusters), they block webserver hosting.

I want to switch to something else.

---

### Post by mestreofmestres on 2008-03-17
One other suggestion, if you're sure your ISP has blocked you, then they have, but looking at your snapshot you posted on your first page, you configured your settings on Virtual Server page, not Port forwading page. You want to enter your info on the port forwarding page, and forward it to 192.168.0.3 to get it to work.

---

### Post by mestreofmestres on 2008-03-17
Also with Fedora, the firewall in Fedora is a bit more picky than Ubuntu's is. You may need to check the firewall in Fedora as well, because it may be blocking external IP's and only accepting internal IP's. But I'm moreso certain that it's your port forwarding that's messed

---

