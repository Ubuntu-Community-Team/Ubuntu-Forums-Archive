---
title: "dlink router stats/hack?"
date: 2011-11-22
forum: Any Other OS
---

### Post by rhodri11 on 2011-11-22
first off sorry if this is in the wrong section - haven't been on this forum in a while.

I'm getting a little worried after looking at my sky dlink router log stats in the security section. Usually i will get hack attempts in the following format:

kernel: Intrusion from a random ip to my external ip address.

sometimes i will get :

kernel: Firewall Log if i have been downloading torrents or accessed my pc through ssh.

but recently i have seen kernel: Firewall from a random ip to one of my  internal ip's . In one day i had 4 attempts from an ip in china to port  80 on my PS3's ip which is 192.168.0.3 (baring in mind i have port  forward 80 and a few other for online gaming)

I also saw kernel: Firewall going from an IP to my girlfriend phone's  internal IP 192.168.0.6. I typed in the whois command in linux terminal  for that one and found that it was an ip from facebook?

so far i havent seen any attempts on my pc's internal IP apart from when ive been doing things. 

Can anyone tell me if this is serious? How would they get access to my LAN IP's?

I cant see what they can do with port 80 on my ps3 but should i close down all the port forwarding and put the ps3 into a dmz? i am running linux mint 10 and have forwarded port 443 for ssh to it but havent seen any attempts at that port yet.

Again sorry if this post is in the wrong section

cheers
rhodri

---

### Post by spynappels on 2011-11-22
They'll be getting to the LAN IP through UPnP most likely, but as this is NATted most likely, the facebook et al addresses are using your public IP and the traffic is NATted to the source (LAN) IP.

Unless they actually connected rather than simply attempted to connect, there should not be any major problems.

---

### Post by rhodri11 on 2011-11-22
> **spynappels said:**
> They'll be getting to the LAN IP through UPnP most likely, but as this is NATted most likely, the facebook et al addresses are using your public IP and the traffic is NATted to the source (LAN) IP.

Unless they actually connected rather than simply attempted to connect, there should not be any major problems.


well this is the weird thing. I unticked UPnP as i decided to port forward the things i needed. i have about 6 ports forwarded on my ps3 and one to my PC.

i'm just confused as to how the NAT'd address are showing up. Seems like whoever is doing this is scanning my network to get my internal ip addresses and trying to connect to them - which says to me that they are getting past my router?

not too worried about the the PS3 port 80 as I cant see what damaged can be done? same with my girfriends phone. if the logs shows my pc's lan ip then do you think it's best to stop all port forwarding?

to change my ip with sky is it just a case of turning the router off overnight?

thanks for your input

---

### Post by Drenriza on 2011-11-22
First thing first.
Is this a wireless router? If you have a wire directly to your ISP,s modem (as i suspect you have) then i cant see a issue. Since they then first need to hack your ISP, find you and connect to you. Which i don't deem likely.

So if you have a wireless router what wireless protection are you using?
If your getting intruders into your network you have an opening somewhere.

---

### Post by rhodri11 on 2011-11-22
> **Drenriza said:**
> First thing first.
Is this a wireless router? If you have a wire directly to your ISP,s modem (as i suspect you have) then i cant see a issue. Since they then first need to hack your ISP, find you and connect to you. Which i don't deem likely.

So if you have a wireless router what wireless protection are you using?
If your getting intruders into your network you have an opening somewhere.


hi

---

### Post by rhodri11 on 2011-11-22
> **Drenriza said:**
> First thing first.
Is this a wireless router? If you have a wire directly to your ISP,s modem (as i suspect you have) then i cant see a issue. Since they then first need to hack your ISP, find you and connect to you. Which i don't deem likely.

So if you have a wireless router what wireless protection are you using?
If your getting intruders into your network you have an opening somewhere.


hi

yes its a sky dlink  wireless router and i habve wpa2 enabled password is strong and cant see them getting through to the wifi so im thinking its a port i have 'open'.

like i say only one port open on the my linux box and that for ssh through 443. 5 or 6 ports open for my ps3 including port 80. 

no ports open at all for any other devices...which doesnt help explain the random facebook ip trying to access the HTC phone?

i was always told to turn UPnP off and port forward but do you think it's best to do the opposite?

cheers
rhod

---

### Post by Hack.The.Pow. on 2011-11-22
why are you forwarding 6 ports to your ps3?  are you actually hosting anything on port 80(web server) on your ps3.  I don't see the need to be forwarding all those ports.  Especially even one for your gf's phone....

---

### Post by Dangertux on 2011-11-22
> **rhodri11 said:**
> first off sorry if this is in the wrong section - haven't been on this forum in a while.

I'm getting a little worried after looking at my sky dlink router log stats in the security section. Usually i will get hack attempts in the following format:

kernel: Intrusion from a random ip to my external ip address.

sometimes i will get :

kernel: Firewall Log if i have been downloading torrents or accessed my pc through ssh.

but recently i have seen kernel: Firewall from a random ip to one of my  internal ip's . In one day i had 4 attempts from an ip in china to port  80 on my PS3's ip which is 192.168.0.3 (baring in mind i have port  forward 80 and a few other for online gaming)

I also saw kernel: Firewall going from an IP to my girlfriend phone's  internal IP 192.168.0.6. I typed in the whois command in linux terminal  for that one and found that it was an ip from facebook?

so far i havent seen any attempts on my pc's internal IP apart from when ive been doing things. 

Can anyone tell me if this is serious? How would they get access to my LAN IP's?

I cant see what they can do with port 80 on my ps3 but should i close down all the port forwarding and put the ps3 into a dmz? i am running linux mint 10 and have forwarded port 443 for ssh to it but havent seen any attempts at that port yet.

Again sorry if this post is in the wrong section

cheers
rhodri

I'm confused. What is the question?

Your router is functioning as it should, if you have ports forwarded then requests on that port will go to the ip of the machine it is forwarded to. In this case your PS3.

Router's are not the end all be all of security many make them out to be.

---

### Post by rhodri11 on 2011-11-22
> **Hack.The.Pow. said:**
> why are you forwarding 6 ports to your ps3?  are you actually hosting anything on port 80(web server) on your ps3.  I don't see the need to be forwarding all those ports.  Especially even one for your gf's phone....

no im not hosting anything. i play a lot of call of duty and there are 5 recommended ports to forward in order to be fully functional online. port 80 was also recommended maybe for when the playstation network chooses me to host the game but im going to delete this so i don't host in future.

with regards to my girlfriends phone...i haven't port forwarded anything for it as i wouldn't need to. that's why i'm confused with the router log saying connection to ip 192.168.0.6 which is her phone. how would anyone even see that ip address available cause it's not?

> **Dangertux said:**
> I'm confused. What is the question?

Your router is functioning as it should, if you have ports forwarded then requests on that port will go to the ip of the machine it is forwarded to. In this case your PS3.

Router's are not the end all be all of security many make them out to be.

OK I understand and agree with what you are saying but it still doesn't account for a connection attempt to my girlfriends phone :-s


thanks for getting back to me

---

### Post by Perfect Storm on 2011-11-22
Moved to Other OS/Distro Talk.

---

### Post by rhodri11 on 2011-11-23
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

apologies for posting in the wrong section but i would have thought this topic is more suited for networking as it's do with a network hack and has nothing to do with linux or any other OS?

again sorry if im wrong it just ive had no input from other members since this moved....?

---

### Post by Perfect Storm on 2011-11-23
> **rhodri11 said:**
> apologies for posting in the wrong section but i would have thought this topic is more suited for networking as it's do with a network hack and has nothing to do with linux or any other OS?

again sorry if im wrong it just ive had no input from other members since this moved....?

If it was on Ubuntu you had the problems, you had posted in the right forums. But Mint is not part of the Ubuntu Family or part of a distro that are supported by Canonical. So your post belongs here or you can try Mint forums.


regards
A.I. Dude

---

### Post by Dangertux on 2011-11-23
> **rhodri11 said:**
> first off sorry if this is in the wrong section - haven't been on this forum in a while.

I'm getting a little worried after looking at my sky dlink router log stats in the security section. Usually i will get hack attempts in the following format:

kernel: Intrusion from a random ip to my external ip address.

sometimes i will get :

kernel: Firewall Log if i have been downloading torrents or accessed my pc through ssh.

but recently i have seen kernel: Firewall from a random ip to one of my  internal ip's . In one day i had 4 attempts from an ip in china to port  80 on my PS3's ip which is 192.168.0.3 (baring in mind i have port  forward 80 and a few other for online gaming)

I also saw kernel: Firewall going from an IP to my girlfriend phone's  internal IP 192.168.0.6. I typed in the whois command in linux terminal  for that one and found that it was an ip from facebook?

so far i havent seen any attempts on my pc's internal IP apart from when ive been doing things. 

Can anyone tell me if this is serious? How would they get access to my LAN IP's?

I cant see what they can do with port 80 on my ps3 but should i close down all the port forwarding and put the ps3 into a dmz? i am running linux mint 10 and have forwarded port 443 for ssh to it but havent seen any attempts at that port yet.

Again sorry if this post is in the wrong section

cheers
rhodri

In regards to your girlfriends phone, I would take a wild guess and say facebook chat, it establishes a direct connection to the client. Port doesn't have to be forwarded because the connection is solicited internally. Again this is a function of a router, people don't understand it, they seem to think that if you don't forward a port the internal systems are innaccessible, this is simply not true.

---

### Post by rhodri11 on 2011-11-24
> **Dangertux said:**
> In regards to your girlfriends phone, I would take a wild guess and say facebook chat, it establishes a direct connection to the client. Port doesn't have to be forwarded because the connection is solicited internally. Again this is a function of a router, people don't understand it, they seem to think that if you don't forward a port the internal systems are innaccessible, this is simply not true.


that makes a lot of sense, thank you very much.

only forwarded two ports for ps3 now and one for my linux box so hopefully no more issues

---

