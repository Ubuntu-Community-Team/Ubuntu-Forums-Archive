---
title: "2 Computers, 1 connection"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-13
Ok, this probably isn't a ? for this forum, but you guys tend to be more knowledgeable than other forums on the net, so here goes.  I have 2 computers, one w/ XP, and one w/ Xubuntu.  I want to split my internet connection so that it can be used equally among the 2 computers.  I don't really want a network b/c i don't need the 2 comps to communicate, and plus I don't even think the 2 OSes CAN be networked, can they?  Anyway, what is the easiest way to do this without spending a million ?'s ?  Thanks in advance for any info you might have for me.

---

### Post by aysiu on 2006-05-13
[QUOTE=brady618]Anyway, what is the easiest way to do this without spending a million ?'s ? [/QUOTE] Get a router. [This one's only US$40](http://www.newegg.com/Product/Product.asp?Item=N82E16833127143).

---

### Post by jazzmuzik on 2006-05-13
Get a router. Some broadband modems have routing capabilities as well.

Or, if you have an old computer, you can dedicate it as a server and use a hub. Use Firestarter to set up IP masquerading. Not too hard, but you'll have to do trial & error and some reading on the net at first until you understand it.

---

### Post by cotcot on 2006-05-13
2 different OS can be networked.
I had 2 PC with each 2 OS on one internet connection (cable). I had to buy a cable splitter (25 euro). If I changed from one PC to the other (whatever OS) I had to release the IP adress ('ipconfig /release' for M$ and 'sudo dhcpcd -k eth0" for linux). I changed my connection. I can now surf with the 2 PC s together because it was an upgrade of my provider at no extra cost.

---

### Post by matthew on 2006-05-13
The easy way (and the way i recommend) is to buy a router. Plug it in, plug each of your computers into it. Problem solved.

The fun way (if you like challenges and want to learn something) is to put a second ethernet card in one of the computers (I recommend using the linux box) and learning how to make it share it's connection. It will involve some reading and work for you, though.

---

### Post by brady618 on 2006-05-13
Now with just a regular router, not a wireless since I don't feel like going out and buying wireless pci cards for both my computers, i'll still be able to connect to both, even though one is linux n the other is windows?  I was looking at this one [http://www.walmart.com/catalog/product.do?product_id=3910287](http://www.walmart.com/catalog/product.do?product_id=3910287) , do you think it'll give me problems?

---

### Post by aysiu on 2006-05-13
Wireless routers are not that much more expensive than wired routers, *and* they also support wired connections.

In our apartment, we have a wireless router, and it has four wired ports. I use the two wired ports for my two Ubuntu computers. My wife uses the wireless antenna for her Powerbook.

It doesn't hurt to have the wireless in there just in case you get a laptop later.

---

### Post by physcsdrk on 2006-05-13
That router shouldn't give you any problems.  Routers don't require software to be put on your computer so they work with any os.

---

### Post by n3tfury on 2006-05-13
[QUOTE=aysiu]Get a router. [This one's only US$40](http://www.newegg.com/Product/Product.asp?Item=N82E16833127143).[/QUOTE]

ding ding.  winnar.  simple *and* cheap.

*edit* ok, i sort of take it back.  a router is still the best option, but i've had NUMEROUS issues with several models of Dlink routers, including that one (overheating, frequent disconnects).  

imo, netgear and especially linksys are much better products.

---

### Post by jazzmuzik on 2006-05-13
The router keeps track of which packets go to which computer, incoming and outgoing, so you can surf with both computers at the same time.

---

### Post by rvergara on 2006-05-13
I strongly recommend Linksys WRT54G

EDIT by matthew: Oh, stink. I'm sorry. I thought I hit "reply with quote" and accidentally hit "edit" and didn't notice that I had greatly amended your post until it was too late. I apologize wholeheartedly--even more so because this was a great post. Please feel free to post your thoughts again.

What a great community this is. This kind of politeness is not easily seen anywhere.

I mentioned in the original post that this router is linux based, which is not very important for the original poster, and plain simple to set up. However, after a user is more experienced you can upgrade this router to evolve it into an industrial strength router (a la Cisco). This upgrade is actively developed by an open source project. The upgraded router has excellent QoS functionality (which is the reason I use it, so I can priopritize Voip packets, while my kids can keep downloading videos and mp3's)

Regards

Ramiro

---

### Post by matthew on 2006-05-13
I second the Linksys WRT54G recommendation. I have one and it is great.

---

### Post by djsroknrol on 2006-05-13
Hi Brady618;

That router from "Wally World" is ok.....if you're using XP.... I replaced my CompUSA generic one for it. It will work in mixed eviros, but it's slow resolving things...works a little better on the static side...spend another 15 or so and get a better one somewhere else...just an opinion on it...

---

### Post by jtibau on 2006-05-13
I configured one of my PCs to do some routing a while ago... It was pretty cool, specially for showing off to some of my friends :)
However there where times I wanted to use the other PC which was connected to the routing PC without having the first one on (to save power). That was kinda bothersome since I had to unplug cables, reboot the cable modem, reconfigure the network, needless to say, I got tired.
So recently I decided to buy a router. Found a linksys and I'm perfectly happy with it. Best buy I've made in a while.

[QUOTE]
Wireless routers are not that much more expensive than wired routers, and they also support wired connections.
[QUOTE]

A friend of mine brought a laptop with ubuntu installed, he hadn't tried a wireless network yet. It was pretty cool to have it working that way. So even if you don't have a laptop yet (I plan on getting one soon) it is still very usefull. I think you will regret it later if you don't buy wireless now because you don't currently use it.

---

### Post by brady618 on 2006-05-13
fake123, wtf, why the hate?  I was just asking a simple question.  Perhaps someone else other than fake123 could answer this (since he's apparently kind of a dink) but what is the difference between a router and a hub?

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=n3tfury]ding ding.  winnar.  simple *and* cheap.

*edit* ok, i sort of take it back.  a router is still the best option, but i've had NUMEROUS issues with several models of Dlink routers, including that one (overheating, frequent disconnects).  

imo, netgear and especially linksys are much better products.[/QUOTE]

I wouldn't go with a Dlink, I have had one for a while, and find more than a couple things with the wireless that are proprietary. Not that you can't work around it, but you shouldn't have to.

I like linksys as well. If you are tricky you can even put a special linux OS on some linksys routers, and run iptables amoung other things.

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=brady618]fake123, wtf, why the hate?  I was just asking a simple question.  Perhaps someone else other than fake123 could answer this (since he's apparently kind of a dink) but what is the difference between a router and a hub?[/QUOTE]

A hub is basically a repeater that sends packets out to every device pluged into it. It is up to your computer to look at all the packets, and then take the ones that that are addressed to it.

A router is used to route packets between 2 different networks (i.e. your ISP's netowrk, and your home network) The advantage to a router is that trafic on yor network, or form other networks goes directly to its destination, instead of going to every host on your network. 

Correct me if I am wrong, but I don't think a hub (if its strictly a hub) will work for internet connection sharing, because it works on the physicall layer, and only knows mac addresses, and not IP addresses.

---

### Post by n3tfury on 2006-05-13
[QUOTE=fake123]i hate you
i wish i could jump throught the monitor and punch you
can people really be that dumb?
get a dlink
if you really wanna be cheap get a hub[/QUOTE]

you're an idiot.

brady, don't listen to that dolt.  if you want to know the differences between a hub and a router, go [[COLOR="DarkOrange"]here[/COLOR]]("http://ask-leo.com/whats_the_difference_between_a_hub_a_switch_and_a_router.html").

*edit* sorry snow, didn't see your above post.  was idle for a bit.

---

### Post by n3tfury on 2006-05-13
[QUOTE=DSn0wMan]
I like linksys as well. If you are tricky you can even put a special linux OS on some linksys routers, and run iptables amoung other things.[/QUOTE]

yeah.  if i recall correctly you have to get <version 5 of the WRT54G.

---

### Post by jtibau on 2006-05-13
Hubs might be cheap, but a router is a much more advanced device... Maybe a while ago a router might've been too expensive to consider for a home network, but at the prices you see now (low in my opinion) it is worth the small investment considering all the features they (routers) come with.
A $50 router like the linksys mentioned, comes with 4 switching ethernet ports, wireless access and works as a firewall, it has a web base configuration, easy to figure out. I bought the "compact" version, it's about the size of 3 stacked diskettes!
A hub definitely doesn't provide that kind of functionality. :)

---

### Post by n3tfury on 2006-05-13
[QUOTE=jtibau]
A hub definitely doesn't provide that kind of functionality. :)[/QUOTE]

...or security.  in my opinion, you're nuts not to have a router if you're using broadband.

---

### Post by jtibau on 2006-05-14
haha :D I just learned how to correctly quote a post:
[QUOTE=n3tfury]...or security.  in my opinion, you're nuts not to have a router if you're using broadband.[/QUOTE]
:D  you're right, however, I only sort of have broadband hehe. I live in south america and believe me everytime I think about how much I pay for internet service I feel insulted...
I currently have 64/64 kbps and I'm paying $55 per month. The ISP has been holding up an upgrade to their system for a while, but even then I'll only get 200/150 kbps.
Anyway it's kinda like the best there is available so it doesn't seem like I have much of an option. I study computer science so it is pretty much a must have.
Well anyways, I bought the router for connection sharing, plus the increased security for my systems. As you said, it turns out it was a good choice.

---

### Post by rvergara on 2006-05-14
[QUOTE=n3tfury]yeah.  if i recall correctly you have to get <version 5 of the WRT54G.[/QUOTE]

That is correct, even though there is a version 5 that is linux based (WRT54GL), just to be on the safe side you can buy any WRT54G, versions 1 to 4 and you will be getting a Linux based prime time router.

Regards

Ramiro

---

### Post by kriding on 2006-05-14
I bought a powerline router from Billion   [http://www.billion.com/product/powerline/bipac7560g.htm](http://www.billion.com/product/powerline/bipac7560g.htm)

that router is capable of wireless and powerline connection (uses your electrical cables as a network) and I have both my systems (one ubuntu, one XP) communicating with each other and on the net...ubuntu required absolutly no configuration on my part at all for access to the network or to use the router.

---

### Post by DSn0wMan on 2006-05-14
I heard about this technology a couple of years ago, its kool that ppl are using it now. I wonder if we have such a device in the US?

Just so I totaly understand - You are using the power wireing in the house instead of running cat5 all over the place.

---

### Post by n3tfury on 2006-05-14
not sure if it's available at your brick and mortar, but i used ehternet over power in a motel recently because i wasn't happy with their wireless.  all it took was a small "converter" from the front desk.  plug and go.

---

### Post by brady618 on 2006-05-14
I don't mean to sound like a broken record or anything, but what would the dif be between this [http://www.walmart.com/catalog/product.do?product_id=3910287](http://www.walmart.com/catalog/product.do?product_id=3910287) and the WRT54G.  I really don't plan on buying anything that's wireless capable for at least a few years.  I'm not in the financial situation to do this currently.  And by the time I have something that would utilize the wireless market, wouldn't v. 1 of the WRT54G be kind of... outdated.  As I understand, the difference between the versions is the speed of the wireless.  So if I buy a laptop or something in 5 years and try to use this, by then "ancient", router, it would be pointless, b/c I could prob buy a WAY better one then for less than I'd be able to buy one now.  So will the one from Wally World suffice for my minimal "wired" needs NOW without harming my current connection speed?  Or would you still suggest the WRT54G?  Oh, btw, the Walmart one is currently on MAJOR discount, and less than half the price of the WRT54G, which they also sell.

---

### Post by n3tfury on 2006-05-14
but you can find the WRT54G on sale for less than that, if you keep your eyes peeled.  the linksys is proven to be a solid router whether you use the wireless capability or not.

---

### Post by brady618 on 2006-05-14
At my walmart, that particular router is on sale for like $28, and I haven't found a WRT54G for less than $60 yet.

---

### Post by n3tfury on 2006-05-14
ok, i might be a little biased here, because i *despise* Walmart.

---

### Post by brady618 on 2006-05-14
Haha, no problem with that.  Walmart = the devil.  But sometimes they got some good stuff on the deal.  To each his own.  But unless I can figure out a valid reason why I shouldn't buy that wired router from there (other than the fact that I can't use my wireless devices (which I don't own and prob won't for quite a while) then I'mma buy it probably tomorrow.  I mean, it IS linksys, so it's gotta be quality.  It just isn't up to current technology standards - i.e. it's not "wireless capable".  Boohoo.  Whatever.  ;)  Thanks for all you're help anyway, guys.  It's great how many courteous people there are on this forum. :D

---

### Post by n3tfury on 2006-05-14
report with a small review after it's hooked up.  i couldn't find a decent review of that device anywhere.  good luck!

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=brady618]At my walmart, that particular router is on sale for like $28, and I haven't found a WRT54G for less than $60 yet.[/QUOTE]

I found a couple different sources for $50, and they have free shipping. I reccomend going to newegg.com they have been pretty good for me.

here is a link with multiple sources.

[http://castle.pricewatch.com/s/search.asp?s=WRT54G](http://castle.pricewatch.com/s/search.asp?s=WRT54G)

edit: OOOOooo $35 after rebate at newegg, and its the compact version

---

### Post by kriding on 2006-05-15
@ DSn0wMan

that's correct, it uses cat5 to connect from the box to the adapter/router, which then just plugs into an electrical socket...sooooo much easier thentrying to route cat5 all over the house, and it means i'm free to relocate either computer without having to replan the cabling, and there is no real noticable degredation in the network...if any

---

### Post by wannabesurfer on 2006-05-15
I recently bought a eth card and cable for my Desktop/laptop, connected them together, The laptop had a modem built in, put the laptop IP on static 
and voila for an amzing sum of less than 10 euro I had it working, 
but, and a big but......... I have not yet managed to do this since i changed to ubuntu on my laptop, having some issues getting online with it.

---

### Post by mips on 2006-05-15
[QUOTE=brady618]Haha, no problem with that.  Walmart = the devil.  But sometimes they got some good stuff on the deal.  To each his own.  But unless I can figure out a valid reason why I shouldn't buy that wired router from there (other than the fact that I can't use my wireless devices (which I don't own and prob won't for quite a while) then I'mma buy it probably tomorrow.  I mean, it IS linksys, so it's gotta be quality.  It just isn't up to current technology standards - i.e. it's not "wireless capable".  Boohoo.  Whatever.  ;)  Thanks for all you're help anyway, guys.  It's great how many courteous people there are on this forum. :D[/QUOTE]

Only downside I see is that it has no built-in adsl modem. So you can't connect it directly to your adsl line, you have to go via a external adsl modem with an ethernet interface.

How is your current internet working ? Hardware etc ?

---

### Post by brady618 on 2006-05-15
I was under the impression that regardless of which router I got, i'd still have to hook my current modem into it.  I'm using a Westell 6100 modem with a DSL connection.  Am I wrong in this understanding?  With the WRT54G, I'd still need my external modem, which would plug into the router, and from there be sent to both of my computers (plus the Xbox, when I'm using Live), right?

---

### Post by n3tfury on 2006-05-15
yes, you are correct.

---

### Post by brady618 on 2006-05-15
Okay, mips confused me there for a second with his talk of adsl lines.  I suppose I could buy a new modem with multiple ethernet connections, but that would probably be more expensive than just buying, say, the WRT54G.  Would the connection be better, though, cutting out the middleman?  Perhaps Verizon might send me a a dif kind of modem if I called them and returned the one they sent me.  I've heard of people getting wireless modems from Verizon and only having to pay a one-time $15 extra or something like that, and it would have multiple ethernet connections.  Anybody with Verizon experience this, or know of anybody whose gotten one of these modems??

---

### Post by catlett on 2006-05-15
[QUOTE=DSn0wMan]I heard about this technology a couple of years ago, its kool that ppl are using it now. I wonder if we have such a device in the US?

Just so I totaly understand - You are using the power wireing in the house instead of running cat5 all over the place.[/QUOTE]
[http://www.netgear.com/products/details/XE104.php](http://www.netgear.com/products/details/XE104.php)

---

### Post by mips on 2006-05-15
[QUOTE=brady618]I was under the impression that regardless of which router I got, i'd still have to hook my current modem into it.  I'm using a Westell 6100 modem with a DSL connection.  Am I wrong in this understanding?  With the WRT54G, I'd still need my external modem, which would plug into the router, and from there be sent to both of my computers (plus the Xbox, when I'm using Live), right?[/QUOTE]

It depends on what you buy. You get wireless/switch/router/adsl modem all-in-one devices like the linksys WAG54G netgear DG834G etc. With these and many others you do NOT have to connect it to your existing modem as they will plug straight into your adsl line.

Sorry for the confusion. It all depends on what you buy/want.

To confuse you even further your Westell 6100 is a 'router' but can function as a modem as well ;)

---

### Post by n3tfury on 2006-05-15
dude, you already have a modem, you don't need anything other than a router.  don't make it harder than it needs to be.

---

### Post by brady618 on 2006-05-16
What do you mean my modem is a router as well as a modem?  It only has two outputs, one ethernet and one usb, and I was reading that you can't use both at the same time.  I wouldn't use USB anyway, too unreliable.  If it is already a router, as you say, then how could I use it to hook up both computers at the same time without having to buy a whole new router?

---

### Post by n3tfury on 2006-05-16
[QUOTE=n3tfury]dude, you already have a modem, you don't need anything other than a router.  don't make it harder than it needs to be.[/QUOTE]

^

---

### Post by mips on 2006-05-16
[QUOTE=brady618]What do you mean my modem is a router as well as a modem?  It only has two outputs, one ethernet and one usb, and I was reading that you can't use both at the same time.  I wouldn't use USB anyway, too unreliable.  If it is already a router, as you say, then how could I use it to hook up both computers at the same time without having to buy a whole new router?[/QUOTE]

Your so called 'modem' can function as a router. But right now i'm about to go watch "village of the dammed" so i'lll reply in the morning...

---

