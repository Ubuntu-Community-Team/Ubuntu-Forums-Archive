---
title: "[SOLVED] Neighbour using router"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Faud on 2008-02-26
My wife is using XP and Im on Ubuntu. We will share files using samba. My wife has noticed that there is a strange person on now when she clicks "view workgroup computers". Is there a way to kick this person off from Ubuntu or do I need to change a setting in my router ?
Its a wireless router but both my wife and I are wired it. Also if I add a password ? or something will it affect my internet on Ubuntu ?
Thanks guys.

---

### Post by Het Irv on 2008-02-26
If you set a password if should not affect wired internet.  A WEP or WPA (I am not sure on the difference) encrypts only the wireless.  You router will assume that all physical connections are approved.

---

### Post by solitaire on 2008-02-26
If you are technically minded

Get the "MAC" address of all your Network cards and Wireless Cards (usually printed on them somewhere) and enter them into the router.

The Router should have an option to filter by MAC codes so you can set it to only accept your devices (even if someone get's your password for the router they won't be able to connect).

But a setting the security is the First step :D

or you could Bill him for the Internet use :D

---

### Post by drunkardivan on 2008-02-26
Installing security is necessary, IMO. WEP is kinda "good enough" if you just want to keep someone off your network. WPA is far better- it really can't be brute-forced. But I've had some issues getting both to work on my wife's old laptop.

So, yes, secure your network, but then be prepared to do some tinkering. You may not have to, but have it in the back of your mind.

(This isn't directed at Faud, since he's wired. It's just in case a new poster sees this and decides to drop wireless security on their router, then can't get online. Faud, use WPA.)

---

### Post by Rucas on 2008-02-26
Hi mate.
Well most routers will have the ability to set up a Wirelless password. YOu should do so, otherwise you are simply ''inviting any unwanted guests'' into your network.
Now to set up the password you should have to access the actual routers set up page via a web browser, or if your's come with a specific software.
Simply use WEP (its the most common and most supported by all wirelless devices) and set up a password .
When this happens your Network will still be visible to all, but only those with the correct password may enter. So when you now try to go onto the Net it will ask for the newlly configured password.
You can even go further by blocking the unwanted guests IP on your router.
Good luck.

---

### Post by shad0w_walker on 2008-02-26
Just as a note, if you have no need for the wireless access just disable it on the router. Fool proof protection.

---

### Post by drunkardivan on 2008-02-26
Oh, MAC adress filtering, not broadcasting the SSID, and WPA combine to give you a nice secure network. I'd encourage any wireless user to go this route.

Also, depending on your router, it may provide you access to your neighbor's computer. Placing "special" pictures- with a note like "quit stealing my internet!" written on the image itself in GIMP or another image-altering program- as your neighbor's background could work quickly to discourage this practice. 

That wouldn't be very nice, though. You maybe shouldn't do that.

---

### Post by Jerry N on 2008-02-26
If you don't use the wireless feature of the router, just turn it off.  You could always turn it back on if needed.  You could also turn off SSID broadcast as well as enabling encryption.

Jerry

---

### Post by amingv on 2008-02-26
If you're not using wireless just disable it altogether:

[QUOTE=Peter Norton's Network Security Fundamentals]
First rule of networking security:
"Disable *right now* all networking features you don't absolutely need.[/QUOTE]

---

### Post by movieman on 2008-02-26
It's worth noting that you neighbour may not even realise they're connected to your network: their computer might be autoconnecting to the first unencrypted wireless network that it sees. I can see six to eight from my house, though fortunately they are all encrypted.

WEP is about as effective against a hacker as a wet paper bag, but it will stop honest people from connecting... it's more of a 'no tresspassing' sign than effective security. You need at least WPA if you want to stop anyone who has a clue and is determined to get into your network.

---

### Post by jonabyte on 2008-02-26
> **solitaire said:**
> 

or you could Bill him for the Internet use :D

Heck I'd call the cops, save your behind if he/she is doing any illegal activity :-P

---

### Post by Crooksey on 2008-02-26
[QUOTE=Z3r0_c00l]image-altering program- as your neighbor's background could work quickly to discourage this practice. 

That wouldn't be very nice, though. You maybe shouldn't do that.[/QUOTE]

I dont think we are worthy.

Add WPA security to the wireless network, sorted.

---

### Post by solitaire on 2008-02-26
Also if your neighbour is doing anything "Illegal" you will probably get the blame. 

Since the broadband is registered in YOUR house. try proving that it was him that D/L'ed Barbra Strisands Full Back Catalogue when the RIAA comes a knocking....

---

### Post by drunkardivan on 2008-02-26
> **Crooksey said:**
> I dont think we are worthy.

Dude, it was a joke. I don't seriously think someone would go to all that trouble, but the thought of the look on the neighbor's face gave me a cheap grin. 

I guess I should have used a smiley face to insure people didn't think I was serious.

---

### Post by Faud on 2008-02-26
Thank you guys for all of the help so far. I was told to type 192.168.0.1.  I did that and nothing happens lol, just trys to load up a web page. Is there something that Im missing ?

---

### Post by Faud on 2008-02-26
Oh, thank you I was corrected. I went to network mode and changed it from "mixed" to "disabaled" on wireless settings. Thanks again yall so much. Marking as solved and adding thanks

---

### Post by Het Irv on 2008-02-26
What kind of Router do you have?  On the linksys routers that address will take you to the router's control panel, which is where you need to be.  It is displayed as a web page....try typing [https://192.168.0.1](https://192.168.0.1) in your web browser.


Nevermind problem fixed....Congrats

---

### Post by Znort_Ubern00b on 2008-02-26
If he is stealing your wireless you can on some routers restrict access to certain ip addresses as well and block sites with certain words in other than on your pc (good if you have kids using internet).

But first instance set up at least WEP encryption 128bit, unless they're determined it will stop them....also report them to police keep a log and get the MAC address of the pc logging on. they are breaking the law and can be charged [see this link]("http://www.theregister.co.uk/2008/02/21/wi_fi_squatting_arrests/"). think the law pretty much applies everywhere...in some form or another.

---

### Post by stchman on 2008-02-26
> **Faud said:**
> My wife is using XP and Im on Ubuntu. We will share files using samba. My wife has noticed that there is a strange person on now when she clicks "view workgroup computers". Is there a way to kick this person off from Ubuntu or do I need to change a setting in my router ?
Its a wireless router but both my wife and I are wired it. Also if I add a password ? or something will it affect my internet on Ubuntu ?
Thanks guys.

If neither you or your wife uses the wireless portion then go into the router and disable the wireless portion.  If your wireless is unprotected then people will leach your bandwidth.  Insecure wireless connections are a no no and should be locked down or turned off.

What can happen is that if somebody else gets on your connection and surfs say kiddie porn the authorities will come to you.  Not worth it.

---

### Post by stchman on 2008-02-26
> **drunkardivan said:**
> Oh, MAC adress filtering, not broadcasting the SSID, and WPA combine to give you a nice secure network. I'd encourage any wireless user to go this route.

Also, depending on your router, it may provide you access to your neighbor's computer. Placing "special" pictures- with a note like "quit stealing my internet!" written on the image itself in GIMP or another image-altering program- as your neighbor's background could work quickly to discourage this practice. 

That wouldn't be very nice, though. You maybe shouldn't do that.

MAC filtering is a waste of time and disabling SSID broadcasts do actually more harm.  The best way besides turning off the wireless transmitter is to use WPA or even better WPA2 and have a very strong passphrase of at least 30 characters with upper, lowercase, symbols, etc.

---

### Post by drunkardivan on 2008-02-27
> **Faud said:**
> Thank you guys for all of the help so far. I was told to type 192.168.0.1.  I did that and nothing happens lol, just trys to load up a web page. Is there something that Im missing ?

Just an FYI- try 192.168.1.1 . Use "admin" as the user name and password.

---

