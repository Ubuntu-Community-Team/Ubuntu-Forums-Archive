---
title: "Dapper Torrents"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-05-20
BitTorrent seems to d/l at a snail's pace.  I know that this is because I am using a router.  I am used to using BitComet which is very easy to select which port to use for torrents.  My question is how do I tell BitTorrent which port to use, or can I install BitComet or something better than BitTorrent?  I did wait considerable time for BitComet to seed--  1/2 hour for a popular file.  The speed did not improve, hence my assumption that it does not have the port open.  I have no problem with opening up a port on the router side, just I have no idea how to tell BitTorrent which port to use.

And yes, I only d/l free files and my ISP does not throttle torrents.

Thanks much, I love this community.

---

### Post by BarFly on 2006-05-20
[QUOTE=BarFly]BitTorrent seems to d/l at a snail's pace.  I know that this is because I am using a router.  I am used to using BitComet which is very easy to select which port to use for torrents.  My question is how do I tell BitTorrent which port to use, or can I install BitComet or something better than BitTorrent?  I did wait considerable time for BitComet to seed--  1/2 hour for a popular file.  The speed did not improve, hence my assumption that it does not have the port open.  I have no problem with opening up a port on the router side, just I have no idea how to tell BitTorrent which port to use.

And yes, I only d/l free files and my ISP does not throttle torrents.

Thanks much, I love this community.[/QUOTE]
Oh, right.  This is not Dapper specific.  I had the same problem with Breezy.  I never bothered to learn how to make it work.  Probabally simple.

---

### Post by dmizer on 2006-05-20
bittornado is available via synaptec on my machine, but i have breezy.

also, qtorrent is available.  i just opened synapetic and clicked on search, and typed "torrent", and it lists all the clients available via synaptic.

most people seem to like bittornado, though i don't care for it.  just personal preference. the gnome standard version seems to do what i need it to do so i don't have any complaints.

---

### Post by user1397 on 2006-05-20
possibly with firestarter the ports could be opened?
in firestarter you could go to policy->outbound policy, and deny service for bittorrent for everyone. then in inbound policy, allow service for bittorrent for your ip address.  that might work.

i personally use azureus, cause im used to it and i like all of the features it has.  its actually quite easy to install, just go to: [https://wiki.ubuntu.com/AzureusHowTo](https://wiki.ubuntu.com/AzureusHowTo)

---

### Post by it.henrik on 2006-05-20
Azureus is the best one out there :) It might steal some resources but its worth it

---

### Post by BarFly on 2006-05-20
Thanks for all the responses.  I am not behind a software firewall as I rely on my router as a firewall.  It is an old Lynksys router.  All I need to know is which port to open up on it and I will be golden.
I never really cared for Azareus.  I know it looks all snazzy and what not, but I just want to d/l my legal files and share them with others.  I could care less about looks, only concerned about speed.

I think I opened up port 6886 for BitTorrent (should not be a problem).

---

### Post by BarFly on 2006-05-20
[QUOTE=dmizer]bittornado is available via synaptec on my machine, but i have breezy.

also, qtorrent is available.  i just opened synapetic and clicked on search, and typed "torrent", and it lists all the clients available via synaptic.

most people seem to like bittornado, though i don't care for it.  just personal preference. the gnome standard version seems to do what i need it to do so i don't have any complaints.[/QUOTE]

Yeah, that works for me!  I installed it and my torrent v. regular download is vastlly improved.  I am also used to using it under Win.  I just installed it and did not alter the settings.  As I am curious, why on Earth is BitTorrent so slow?

Thank you all so much!

/Listening to <i><b>Pink Floyd</b>Animals</i>Probabally messed up the tags, but thanks!

---

### Post by user1397 on 2006-05-20
[quote=BarFly]Thanks for all the responses.  I am not behind a software firewall as I rely on my router as a firewall.  It is an old Lynksys router.  All I need to know is which port to open up on it and I will be golden.
I never really cared for Azareus.  I know it looks all snazzy and what not, but I just want to d/l my legal files and share them with others.  I could care less about looks, only concerned about speed.

I think I opened up port 6886 for BitTorrent (should not be a problem).[/quote]
i don't think azureus is "just for the looks"
it has a lot more feautures and information about your torrents than any other bittorrent clients, if you like knowing how your torrents are coming along (like me :))

---

### Post by TheFourElements on 2006-05-20
I have the same problem. My download rate is very rarely above 10-15 but my upload rate often around 40. I just have the bittorrent package installed. Am I to understand that there are better ones?

---

### Post by BarFly on 2006-05-20
[QUOTE=TheFourElements]I have the same problem. My download rate is very rarely above 10-15 but my upload rate often around 40. I just have the bittorrent package installed. Am I to understand that there are better ones?[/QUOTE]
My Canuck (just kidding) friend.  BitTornado works for me thanks to an above poster.  Still, there must be a simple way to have the default torrent program to use a certain port...  I am happy with this solution.

/now listening to Grateful Dead Terrapin Station Disc 2!

---

### Post by TheFourElements on 2006-05-20
[QUOTE=BarFly]My Canuck (just kidding) friend.  BitTornado works for me thanks to an above poster.  Still, there must be a simple way to have the default torrent program to use a certain port...  I am happy with this solution.

/now listening to Grateful Dead Terrapin Station Disc 2![/QUOTE]

Is your only solution using Bit Tornado? I don't know if this info will be important or not but I am using a wireless network and the router is installed on a (gasp) Windows XP machine.

---

### Post by Sef on 2006-05-20
I use bittorrent, and I find the download rate varies greatly.  At times the rate has been 5-10 kb, yet this morning it was super fast about 950 kb: downloaded Dapper in about 12 mintues.   Just have to hit the right time I guess.

---

### Post by skippy81 on 2006-05-20
AFAIK all bittorrent traffic uses the port range 6881-6889.  You need to:

a) Drop the routers firewall on those ports.
b) set up port forwarding to direct traffic on those ports to the internal mac/ip of your linux computer.  Make sure you forward the entire range (6881-6889) on both TCP and UDP.

---

