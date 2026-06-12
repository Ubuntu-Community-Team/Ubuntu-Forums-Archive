---
title: "Need some info"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Porta on 2006-05-21
Hi there
I have a question about a site i visit once in a while and witch is run by a member of this board i think.
Whenever i surf to that place my firestarter gives alert from the following IP-adress;
139.134.5.6.
The sight i mean is wxw.users.bigpond.net.au/hermanzone.

regards

---

### Post by meng on 2006-05-21
Looks like 139.134.5.6 ==  [www.users.bigpond.net.au](www.users.bigpond.net.au)

---

### Post by Porta on 2006-05-21
I've tracked it back to something called Telstra.net, but what have they got to do with the aformentioned site and why try to enter the computer in a unsolicited manner? Not that they have any change ofcourse. :D  

regards

---

### Post by macdo on 2006-05-21
I can tell you this much: telstra own Bigpond, so that's why it's their IP address.

---

### Post by meng on 2006-05-21
Exactly. Or, in slightly more detail, Telstra (which used to be called Telecom Australia) is Australia's largest telecommunications provider, and their internet service is nicknamed Bigpond.

---

### Post by Porta on 2006-05-21
Ok, thanks for the info people.

greetings

---

### Post by Herman on 2006-05-21
Thank you for bringing that to my attention, I would never knowingly run a site that would be in any way hazardous to anyone's computer or their privacy.
All I can say is this is the first I have known of such a thing and it has nothing to do with me.
Telstra Bigpond is a reputable firm and they are quite a popular ISP here in Australia. I don't think they would have any interest in connecting to people's private computers, it's probably something to do with the way they count the bandwidth from the site in case it goes over my limit or something.

Would you like to help me investigate this matter a little further?
Here's an index of all the other Bigpond Broadband Member sites. [http://users.bigpond.net.au/](http://users.bigpond.net.au/)  Please visit a few of the other sites at random and see if the same thing happens at other similar sites or not and let me know. If my site is the only one that does this I will be giving Bigpond a phone call to enquire about this later in the day.
Thank you, Regards, Herman :D

---

### Post by richbarna on 2006-05-21
Sounds to me like Firestarter just detected them trying to send a cookie or a pop-up ad.
Obviously this sort of stuff normally goes unnoticed in windows.

---

### Post by Porta on 2006-05-21
Herman, i will visit some of the sites you mentioned and let you know what happened.
I've visited your site while using windows and i didn't saw or find anything unusal in the firewall-log.

greetz

---

### Post by Herman on 2006-05-22
> Herman, i will visit some of the sites you mentioned and let you know what happened.
I've visited your site while using windows and i didn't saw or find anything unusal in the firewall-log.Thanks, Porta, I called Bigpoand webhosting tech support anyway and asked them about it. There are some great people working for Bigpond and they are very helpful and freindly. That's why I stick with them as my ISP.
The gentleman I spoke to suggested that possibly your firewall might be misconfigured slightly and it might be 'prompting for outgoing connections on port 80' (or something like that). Sorry if that answer has lost some accuracy in the relaying of it, I have a lot to learn about networking and internet.
If your firewall is set hypersensitive though, wouldn't the same thing happen at every website you visit?
Conversely, it's odd that no-one has complained of this sooner? My website has been running for quite a while now, maybe almost a year. I think I started it just a month or two before 'Breezy' was released, because I remember all the work to update it to 'Breezy'.
I will be interested in any more details anyone can provide and Bigpond will probably be interested also, especially if more details can be included such as port numbers or whatever feedback your firewall might provide.
Safe surfing, Regards, Herman :D

---

### Post by Herman on 2006-05-22
> Sounds to me like Firestarter just detected them trying to send a cookie or a pop-up ad.
Obviously this sort of stuff normally goes unnoticed in windows. There should be no cookies or pop-ups or anything like that coming from my website, and I also have even been careful to try and avoid including links to any other websites that have those things if I am aware of them.
Well, cookies are pretty hard to avoid, even Ubuntu Web Forums have those.  (But Ubuntu Web Forums are a trusted source, so we don't mind). If these things are coming from my site though, they should not be, I didn't put any there or give permission for anyone else to do so. If anyone is getting that kind of thing from /hermanzone/ I want to know about it and I'll try and do something about it if anything is happening that shouldn't be. :D Regards, Herman.

---

### Post by adam.tropics on 2006-05-22
It's not you Herman, it's 'them ! With default firstarter settings, every bigpond site does this. Except, those that just have a bigpond placeholder (site under construction etc etc). But if you 'relax' firestarter a bit,  then all is well! I really don't know much about this, but maybe if not cookies then something to do with stats data collection. They all do that!

---

### Post by Porta on 2006-05-22
Herman, i went to the main site 'users.bigpond.net.au' and the firewall reacted;
port; 57303, protocol; TCP, source;139.134.5.6
The second site i visited was 'a-theory-of-mind' and the firewall gave back the following.
port; 57306, protocol; TCP, source; 139.134.5.6
After this i visited several other sites in the domain, including yours and i got no alerts anymore.It only seems to happen when i first get there, i've tested this by shutting down the browser and after that starting again by surfing to bigpond again and lo and behold, the firewall started jumping around again.

What i see is that it's not comming from your site or any site in that domain for that matter, the IP-adres is from Telstra-internet.
The strange thing for me is that this box is behind a router aswell, i've installed firestarter just to play around with.So when i communicate with a server on the internet via port 80 using my browser and a packet for an unopened port arives at the router, it should be dropped like a hot patato.

So that's it, i will test the router at Shields-up (grc.com) to make sure there aren't any open ports i don't know of.

For your information, i have firestarter only configured for the usual things like HTTP,HTTPS,POP3,SMTP and SSH in a outgoing direction.

regards
Porta

---

### Post by Porta on 2006-05-22
I've tried it out with windows XP and netbios-ns kicked in on port 137.It was trying to sent info to IP 144.135.18.32 (Telstra-internet).I have this blocked ofcourse.
This is not a good thing, i don't know what they are doing over there but i think it's quite stupid to play around with netbios.
I've tested the router and all was oke.

regards
Porta

---

### Post by Herman on 2006-05-22
Okay, thanks you fellows, I'll check up on why that happens as soon as I get some time, right now I really need some sleep. Thanks, Herman

---

### Post by Porta on 2006-05-31
Herman are you out there?, is there any news from the australian front on this matter?
If you hadn't have the time yet to get the info, no worries, i ain't going no place and will wait patiently for things to come. :) 

greetings
Porta

---

### Post by Herman on 2006-05-31
Hello, Porta, I have no new information, I did call Bigpond Tech support again, but a different operator in a different department.  I even gave the link to this thread so they can read it themselves. They agree with the first tech support rep said previously, that you might have hypersensitve firewall settings and it's picking up something harmless. 
It will be a long time before I will be able to study networking enough to have an informed opinion myself. My feeling is also that it would be something harmless.
Thanks for your help in letting me know, I will now pay more attention if anything new happens regarding this type of occurence.
Regards, Herman.

---

### Post by confused57 on 2006-05-31
[QUOTE=Herman] They agree with the first tech support rep said previously, that you might have hypersensitve firewall settings and it's picking up something harmless. 
It will be a long time before I will be able to study networking enough to have an informed opinion myself. My feeling is also that it would be something harmless.
Thanks for your help in letting me know, I will now pay more attention if anything new happens regarding this type of occurence.
Regards, Herman.[/QUOTE]

I have a Linksys router and I almost never get an incoming probe firewall alert...I started getting one occasionally and realized I'd get one every time I visited newegg.com.  It wasn't recognized as "serious" by Firestarter, I did the "whois" on the IP address and it was the same one every time.  I essentially have the default IPTable settings, so I'm assuming it's harmless.  Maybe this is the same sort of thing as you're experiencing.

---

### Post by Porta on 2006-05-31
I don't think it's malicious either, but i got curious because it never happens on other sites.
And thanks Herman for your efforts in this case. ;) 

regards
Porta

---

