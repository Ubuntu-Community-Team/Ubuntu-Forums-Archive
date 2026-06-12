---
title: "Wireless at Home"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by tc10b on 2006-05-30
Hi, I know this isn't a strictly Linux question, but I am thinking I would like to start a wireless network at home as it would make it easier for the internet to be shared amongst the household.

I was just wondering if anyone has any suggestions on how to do this and get it to work with Ubuntu, I currently have two laptops which are running Breezy and later Dapper.

Thanks


Tom

---

### Post by rado_london on 2006-05-30
Well Get a wireless router (mine is NETGEAR). Then buy supported wireless cards. To activate and setup the router you need cable connection. Everything is explained in the manual and it is through web interface so it doesnt matter the OS. 
Good luck

---

### Post by popkid on 2006-05-30
[QUOTE=tc10b]Hi, I know this isn't a strictly Linux question, but I am thinking I would like to start a wireless network at home as it would make it easier for the internet to be shared amongst the household.

I was just wondering if anyone has any suggestions on how to do this and get it to work with Ubuntu, I currently have two laptops which are running Breezy and later Dapper.

Thanks


Tom[/QUOTE]

It really depends on your laptops, do they have wireless built in? If so then you may have to use ndiswrapper (an application that uses the windows drivers for the card under linux) to get them working with ubuntu depending on the chipsets they use for wireless (especially with breezy, dapper has better built in wirless support) if you need to get pcmcia wireless cards, you can make life easier for yourself by getting cards with chipsets supported directly in linux (though you should be able to get just about anything working with a little patience and fiddling!)

On the router side, it doesn't really matter which brand you go for, it's separate from your os, most modern wireless routers are configured by a html (web-page effectively) that is actually hosted by the router itself, so you just plug it in and browse to the address of your router on your local network (typically 192.168.1.1) in firefox or whatever browser you are using and configure it from there, if you have adsl broadband then the easiest option is probably to go for a combined broadband modem/wireless router

Do you also want to include desktops..? I'm not so sure how wireless PCI cards are supported in ubuntu, but probably similar to pcmcia, some will be better supported than others.

The only other advice I would give is to steer clear of the USB wireless adpaters available, they seem to cause particular difficulties.

Any more specific questions then post back and I'll try to help, or someone else will!

pK

---

### Post by hw-tph on 2006-05-30
Get supported cards (not "supported" as in ndis drivers but real Linux drivers) but also make sure they do WPA. Setting up WPA in Linux is described, amongst other places, [in the wiki](https://wiki.ubuntu.com/WPAHowto).


Håkan

---

### Post by tc10b on 2006-06-15
Well I bought a card actually, that was listed in the wiki as being supported and thought I'd test it out with the university wireless access points and it doesn't work.

I bought 2 of the 3COM 3CRSHPW196 cards for the two laptops, Compaq Armada M700 and Thinkpad T23, but neither will connect to the network under dapper.

Thanks for all the suggestions, I really appreciate it.

---

### Post by popkid on 2006-06-15
Hi, if you post the difficulties you are having then I'm pretty sure someone will be able to get you going

Sorry to hear it hasn't gone too smoothly so far

pK

---

### Post by tc10b on 2006-11-05
Hi

Right, I now have a router, and I'm now able to share the internet between my two computers, by a mixture of a wired and wireless connection.

I have a printer and would like to share it with the other computer, but have absolutley no idea how I could do that.

Could anyone help me?

---

