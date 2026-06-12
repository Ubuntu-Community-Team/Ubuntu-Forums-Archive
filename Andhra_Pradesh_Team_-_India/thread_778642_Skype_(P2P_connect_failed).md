---
title: "Skype (P2P connect failed)"
date: 2008-05-02
forum: Andhra Pradesh Team - India
---

### Post by jaknap on 2008-05-02
Hi,
Can u help to sort out the problem of Skype. When I connect to Skype it gives me error of P2P connect failed. Please suggest me, what to do. and my Skype is behind proxy server.

Pranky.

---

### Post by RyanTMulligan on 2008-08-30
You can solve this problem by opening xterm and typing:

```
rm -rf ~/.Skype
```

this will delete all of your settings but then it works. At least this fixed it for me.

---

### Post by sakhi on 2009-07-01
Could you retrieve your chat logs? (Chat history) after doing rm -rf in the .Skype directory.

---

### Post by cosimix72 on 2009-11-07
Hi Ryan
where do I find xterm?

thanks in advance...

I GOT IT AND IT WORKED.... MANY MANY THANKS RYAN!!!!

---

### Post by slig on 2009-12-08
Worked for me too! 
Thanks!

---

### Post by eeuzc on 2010-04-13
Hi,
Its not working for me yet. It shows HTTPS auth proxy failed.
I am working under a proxy server that requires authentication.

Any more ideas at how I can get skype working?

---

### Post by hyfanious on 2010-05-16
hi
i've got same problem
im living in iran
i use your-freedom for filtering and change some of my settings
and now can use my skype
if u want tell me to explain my method

---

### Post by cayman1021 on 2010-08-16
It's worked for me too!
I am using Skype 2.1 beta on Ubuntu 10.04
Why will this happen?
This sucks because it wastes my whole morning.:(

---

### Post by GavinWiggins on 2010-10-17
It worked for me in Ubuntu 10.04.  Thanks so much!

---

### Post by ThomasNovin on 2010-12-22
Right now Skype doesn't work and I get this problem. However I think they have technical problems.

I also cannot reach [http://forum.skype.com](http://forum.skype.com) and [https://support.skype.com](https://support.skype.com).

So have that in mind, not always a local problem.

---

### Post by gad2103 on 2010-12-22
i'm having the same issue but i think it also might be on skype's end since the last poster was 32 min. ago.

---

### Post by Somnus07 on 2010-12-22
Also not working for me either. The support site looks like it is back (but the forum is also still down) so yes looks like skype's problem

---

### Post by White-Energy on 2010-12-22
I have the same problem.. i tried it everywhere.. even on my HTC's skype.. you guys know what the result was? 
> NOT WORKING :(

---

### Post by johnnyb0y on 2010-12-22
Same for me here in the UK on 10.04, so I think I'll probably skip the advice to remove the skype directory and let the problem fix itself.

I noticed also that my parents Skype (Windows XP) aborted today, so I downloaded the latest version. Strangely, the Check for Updates failed to work?

Now it all makes sense... it would appear to be Skype at fault :-)

---

### Post by kv300 on 2010-12-22
Wow massive skype failures!! is it 2012?

---

### Post by simplygades on 2010-12-22
> **kv300 said:**
> Wow massive skype failures!! is it 2012?

Same here: p2p connect failed.

I think the the "2012 (End Of The World)" has begun from Skype servers. I need to confess...:p

---

### Post by gangsterkb on 2010-12-22
Skype fails. p2p connection failed...
Hope it will be resolved soon

---

### Post by midion on 2010-12-22
Skype is down you can google it.

---

### Post by ndstate on 2010-12-22
Skype seems to be working now!

---

### Post by ndstate on 2010-12-22
> **pmp6nl said:**
> Skype seems to be working now!

Its back down again :(

More info at [http://blogs.skype.com/en/2010/12/skype_downtime_today.html?cm_mmc=PXTW|0700_B6-_-downtime-20101222](http://blogs.skype.com/en/2010/12/skype_downtime_today.html?cm_mmc=PXTW|0700_B6-_-downtime-20101222)

---

### Post by ephebus on 2010-12-22
Same thing here for me, in Portugal... they say we are 40 years behind the rest of europe, but when Skype crashes *then* we're on time.

And here I was, thinking my country would survive 'till 2052.

---

### Post by Mr.Goose on 2010-12-22
Here in Old Blighty, Skype showed vague glimmers of life a couple of hours ago. I.e. we could actually log in!. However, we could not connect to anyone, not even the Skype Call Test Service.

Now we cannot even log in at all. Tried on several machines. Mrs Goose tried her account too. Same silly red message:- "P2P connect failed".

Seems Skype's so-called *supernodes* are currently *super no's*. Lol. ;)

Definitely a problem with Skype and not our faithful ole 'Bunty!

Best wishes, G.

---

### Post by Mr.Goose on 2010-12-22
Update!

Just logged in to Skype! Yippee! Still can't actually connect to anyone though. :-(

Ho hum. I'm going to forget about Skype for the evening and crack open a bottle of Old Speckled Hen instead. Who knows, I might even get some work done too! lol. 

Mind you, I blame Mrs Goose. I reckon that she single-handedly broke Skype by chatting to so many of her friends simultaneously, that she wore out their batteries - or something. ;-)

Good night all! G.

---

### Post by cgroza on 2010-12-22
Same here. I thought it is a local problem, tried 2 PCs and it did not work. Then I tried my Windows install and it logged in but could not connect to anyone!
Hope this gets fixed quickly...

---

### Post by matt-fender on 2010-12-22
Same problem, UK, Bunty 10.04 :( hopefully they'll have it sorted soon

---

### Post by bond17_007 on 2010-12-22
Looks like Skype problem:
See Quote below from Skype.

As I was trying, it just started working for me now.

Good Luck to others!

> 
Skype downtime today
Earlier today, we noticed that the number of people online on Skype was falling, which wasn’t typical or expected, so we began to investigate.

Skype isn’t a network like a conventional phone or IM network – instead, it relies on millions of individual connections between computers and phones to keep things up and running. Some of these computers are what we call ‘supernodes’ – they act a bit like phone directories for Skype. If you want to talk to someone, and your Skype app can’t find them immediately (for example, because they’re connecting from a different location or from a different device) your computer or phone will first try to find a supernode to figure out how to reach them.

Under normal circumstances, there are a large number of supernodes available. Unfortunately, today, many of them were taken offline by a problem affecting some versions of Skype. As Skype relies on being able to maintain contact with supernodes, it may appear offline for some of you.

What are we doing to help? Our engineers are creating new ‘mega-supernodes’ as fast as they can, which should gradually return things to normal. This may take a few hours, and we sincerely apologise for the disruption to your conversations. Some features, like group video calling, may take longer to return to normal.
Enterprise products including Skype Connect and Skype Manager continue to function normally.

Customers using the enterprise version of Skype for Windows may still experience delays signing in.

Stay tuned to @skype on Twitter for the latest updates on the situation – and many thanks for your continued patience in the meantime.


---

### Post by Der_Kommissar on 2010-12-27
I can connect on my phone, but through Ubuntu (10.04) I keep getting the "P2P connect failed".  removed my folder, then trying to remove skype completely using Synaptic.  Reinstalled.  Still getting it.

I removed a USB headset at the end of a voice call, and that is when my problems began.  I could have done something in the incorrect order, but ... I've had such a frustration with Skype and Ubuntu.  I use it under Windows (XP and 7), Mac OSX 10.6.x, and Ubuntu 10.04.  Only Ubuntu gives me these problems so far. :|  We use it to communicate at work, so it's kinda frustrating when it is always giving me trouble.

---

### Post by ThomasNovin on 2010-12-29
This is what caused my problems:

[https://support.skype.com/en/faq/FA10908/I-was-affected-by-the-December-outage-what-should-I-do;jsessionid=8193A8C80D391BA0A3D32B8F263F133D?frompage=category](https://support.skype.com/en/faq/FA10908/I-was-affected-by-the-December-outage-what-should-I-do;jsessionid=8193A8C80D391BA0A3D32B8F263F133D?frompage=category)

When I start Skype now I'm logged in within a second.

---

### Post by ndstate on 2011-01-01
Anyone else having problems with lots of freezes/dropped calls?

---

### Post by kxhitiz on 2011-04-17
Just go to the skype setting and change the incoming connection port number

---

### Post by pendrive on 2011-09-13
it works for me too, thank you dude

---

