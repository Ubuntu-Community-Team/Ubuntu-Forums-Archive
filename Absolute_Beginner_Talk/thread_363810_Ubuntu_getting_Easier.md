---
title: "Ubuntu getting Easier?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2007-02-17
Don't tell me I do not love Ubuntu because I do but after spending  three months trying to get a USB54G modem configured so that my kids can run their 2 computers from their bedroom, I have gone back to Windows. 

Now I see that Linspire and Ubuntu are teaming up and since my only real problem with Ubuntu was getting connected wirelessly I am wondering will this deal result in better driver compatibility and can I expect to see these changes soon?

I have enjoyed working through the process of learning to do things in Linux and the community has been most helpful only wish I were a bit smarter in figuring out some of these things. I can't wait to come back to Ubuntu.

Also I still say we need a magazine something along the lines of what Lotus did for 123 years ago ( sorry I am dating myself)

Thanks

---

### Post by tronica on 2007-02-17
The only changes i know of is that ubuntu will be using CNR, (click and run). As for more compatibility, every release has more support for more hardware.

---

### Post by aysiu on 2007-02-17
> **clemkonan said:**
> 
Now I see that Linspire and Ubuntu are teaming up and since my only real problem with Ubuntu was getting connected wirelessly I am wondering will this deal result in better driver compatibility and can I expect to see these changes soon? I doubt it.

Linspire and Ubuntu are teaming up to make software installation better/easier or, if you believe the anti-CNR folk, to offer another option for installing software.

It has **nothing** to do with drivers and third-party support. If you do see Ubuntu in your future, keep this in mind when you make hardware purchases:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by tronica on 2007-02-17
also whats the exact modem your referring to?

---

### Post by aysiu on 2007-02-17
By the way, if you haven't totally given up, [this HowTo](http://72.14.253.104/search?q=cache:rGtyTiGCE28J:www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html+WUSB54G+modem+linux&hl=en&lr=lang_en&strip=1) may help you.

I went with the Google cache because the page had trouble loading, but for the future, you may want to try [the original link](http://www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html).

---

### Post by clemkonan on 2007-02-17
My stick is a Linksys USB54G ver4 and I was running Edgy.

The thing that really messed me up was the myriad of options. I wanted to use the Ralink driven rather than nddiswrapper but either way I simply could not get straight instructions. Bear in mind "straight" is a relative term we all learn differently and what is very simple for one person may be quite muddled for someone else.

My mistake also was not dual booting, then we would have had functionality and could have experimented with getting wireless set up rather than being pushed for time.

---

### Post by TheWizzard on 2007-02-17
> **clemkonan said:**
> Don't tell me I do not love Ubuntu because I do but after spending  three months trying to get a USB54G modem configured so that my kids can run their 2 computers from their bedroom, I have gone back to Windows. 


if you have more than one computer, i'd advice you to buy an ethernet modem and a router (or a combi). this makes life a lot easier. also in windows.

---

### Post by clemkonan on 2007-02-17
I am limited to the modem router, a Steedstream 6520 provided by Bell Sympatico. This is a DSL phone modem.

I also have a Linksys WRT54G is this an Ethernet modem?

Why would an Ethernet solution be better, educate me, please

---

### Post by louieb on 2007-02-17
> **clemkonan said:**
> I am limited to the modem router, a Steedstream 6520 provided by Bell Sympatico. This is a DSL phone modem.
I also have a Linksys WRT54G is this an Ethernet modem?
Why would an Ethernet solution be better, educate me, please
You have to go back to the 1990's to find any type of high speed connection that does not use Ethernet and twisted cable. You already have Ethernet running out your ears. [http://en.wikipedia.org/wiki/Ethernet](http://en.wikipedia.org/wiki/Ethernet)

Your Speedstream 6520 is combo DSL modem and router. and it has Ethernet connectors on the back. It is also a wireless router. 
Your [Linksys]("http://en.wikipedia.org/wiki/Linksys_WRT54G") is  also a wireless router with Ethernet connectors on the back. 

Because you have two wireless routers there could be some confusion going on.
Wireless connections are  pretty much standard between the NIC  (Network interface card, your  Linksys USB54G is an example of a NIC) and the router. All brands of NIC's and routers use the same language (802.11) to speek to each other.

The trouble with Linux and wireless is getting the computer to to talk to the NIC. I don't know why wireless is such a problem. Especially when I have plugged in any old wired NIC in and run cable to the router and it just works.
You may want to look at a hardware compatibility list and find a wireless card or stick that is Linux friendly.

---

### Post by GameManK on 2007-02-17
> **clemkonan said:**
> Don't tell me I do not love Ubuntu because I do but after spending  three months trying to get a USB54G modem configured so that my kids can run their 2 computers from their bedroom, I have gone back to Windows. 

People are getting confused because I think what you're referring to as a ***modem*** is a ***wireless card***.

---

### Post by TheWizzard on 2007-02-18
> **GameManK said:**
> People are getting confused because I think what you're referring to as a ***modem*** is a ***wireless card***.

i think you're right, but what about the "kids can run their 2 computers from their bedroom". shouldn't have to do anything with the guy's pc, right? 

i'm a bit confused, i'm affraid :confused:

---

### Post by clemkonan on 2007-02-20
Fair enough, my connection to the internet is via my Speedstream which is a combination Modem / Router.

My WRT54G Linksys Router is not part of the equation its on the shelf because unless I am mistaken it cannot connect to a phone line it needs cable.

My remote connection is through a WUSB 54G  wireless adapter.

Connecting a computer directly to the router is a breeze.

Getting connected remotely via the wireless adapter is a nightmare.

Thanks for all the feedback

---

### Post by halitech on 2007-02-20
as the old saying goes, a router is a router is a router and it doesn't care if you have a cable connection, DSL or just simply have 4 computers in a basement with no internet connection. 

so you connect your computer to the speedstream (which if I understand, works correctly) and you have a wireless card in your computer and also in the kids coputers and there is where the issue is coming up. The kids cannot connect to your computer over the wireless connection.

Am I right so far?

---

### Post by GameManK on 2007-02-20
Quite frankly my suggestion to you is to go buy a Linux compatible card.  It's not working at all vs. some ridiculous how-to everytime you install vs. put it in and voila (easier than windows)!  

I've heard USB cards are particularly difficult to get working.

EDIT: of course if that's not an option, get all the info you can get on the card and the chipset and we'll try to find the right how-to for you

---

### Post by Spr0k3t on 2007-02-20
The WUSB54G will require ndiswrapper to work properly.  Many people have been able to get this wireless connection to work but not without problems.  I'd recommend reading through the forums on [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) to see if you find any similarities with your connection setup.

As it stands, the current network topology is rather confusing in the way you have described it.  The router (Speedstream 6520) is currently connected via USB from your main computer and you are "sharing" the network connection from the connected computer to the kids computer?  This is a little wrong in my opinion, but can be done if no other way is optional.

What needs to be done, instead of an a-b-c type connection, it should be connected as a hub and spoke connection.  This way it would not matter if either computer system is on or off, they would both have connectivity as needed.

So here's the breakdown... start with getting ethernet connectivity on one computer system and turn off all the wireless security for now.  On the other computer with the wireless WUSB54Gv4, get it connected to the Speedstream 6520 router and then change the security settings on the router to accommodate the settings you know will work.  If all else fails, use the router to filter MAC addresses.

The hub and spoke method should be much easier than dealing with internet sharing on Windows.  Your area of concern will likely be the wireless USB card.  I'm going to keep my eye on this thread so I can offer any help along the way.

---

