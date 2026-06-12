---
title: "Basic questions about using/installing"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by tamara_meske on 2007-05-06
Hi, I'm new. Thanks in advance for your help!

I've downloaded the feisty cd image and can run it from my laptop just fine (so far), except for the fact that I am unable to connect to my wireless connection when running Ubuntu from the cd (I haven't installed it yet). The network manager sees the network, but I get the "restricted driver" thing. Also, I have no sound, but I think I can fix that second if I can get the wireless thing fixed.

My wireless connection is encrypted with a 10 digit number (I don't know what kind of encryption this is) but the network manager asks me for something - a WEP 128 passcode I think - but it never connects.

Does functionality change from running from the cd to actually installing? What is the "restricted driver" thing about?

I am ditching Vista and switching completely over to Ubuntu, just as soon as I can get the wireless thing worked out.

I have a lot of questions, but I guess this is as good a place to begin as any. Thanks again.

---

### Post by starcraft.man on 2007-05-06
> **tamara_meske said:**
> Hi, I'm new. Thanks in advance for your help!

I've downloaded the feisty cd image and can run it from my laptop just fine (so far), except for the fact that I am unable to connect to my wireless connection when running Ubuntu from the cd (I haven't installed it yet). The network manager sees the network, but I get the "restricted driver" thing. Also, I have no sound, but I think I can fix that second if I can get the wireless thing fixed.

My wireless connection is encrypted with a 10 digit number (I don't know what kind of encryption this is) but the network manager asks me for something - a WEP 128 passcode I think - but it never connects.

Does functionality change from running from the cd to actually installing? What is the "restricted driver" thing about?

I am ditching Vista and switching completely over to Ubuntu, just as soon as I can get the wireless thing worked out.

I have a lot of questions, but I guess this is as good a place to begin as any. Thanks again.

Ummm, its advisable to plug in an ethernet line for now, wireless is still an iffy thing to set up and likely something you should do after you finish updating and installing everything you need to. I do find it worrisome that you don't know what kind of encryption you are using. I STRONGLY advise you to use at least WPA Personal/with TKIP (WPA2 isn't necessary really, original still works fine). WEP is of no security value, it is a broken encryption and any moron with the right program can crack wep in under a minute. I've seen it done live, its a very real threat, not only can someone then use your internet connection, they can breach your network. Just a notice of security.

I'm fairly sure the sound should fix itself when you install. So install it as you like and when your done we will work out your little bugs with Wireless :)

---

### Post by rygar on 2007-05-06
i'm also new to Ubuntu, but...

i believe your internet connection should work when running ubuntu off the livecd, just as it should when you install ubuntu on your computer.

it's possible ubuntu is not trying the right encryption method for connecting to your network.  ensure that you have the right encryption method selected when you enter your key into ubuntu or else it will probably just say "connecting..." forever.

i know for my wireless router, i have to manually select WPA/TKIP or it won't work.  i can't say what yours uses.

if you can log on to your router through Windows, you can check what security protocol your network uses.

---

### Post by tamara_meske on 2007-05-06
> **starcraft.man said:**
>  I STRONGLY advise you to use at least WPA Personal/with TKIP (WPA2 isn't necessary really, original still works fine). WEP is of no security value, it is a broken encryption and any moron with the right program can crack wep in under a minute. I've seen it done live, its a very real threat, not only can someone then use your internet connection, they can breach your network. Just a notice of security.
Thanks for your input on the security thing. I'm not worried, though - the only reason there's even a security code is because it's the default setting with my modem - it just came with it. That's why I don't know what it is - because it's of no concern to me (until now)! But I checked, and it is indeed a WEP code. Ugh. I almost want to take it off altogether because it's so lame:)

 > **starcraft.man said:**
> So install it as you like and when your done we will work out your little bugs with Wireless :) 
Thanks again for that! I'm really excited to make the switch - ever since I bought this laptop with Vista on it, I have been continually frustrated. I've been a windows user for a long time, but it's never quite worked the way I thought it should. XP was tolerable, but Vista is the bane of my existence and I refuse to shell out another penny to MS for an inferior product. Not to mention that  Firefox, Amaya, the Gimp and other programs don't work right with Vista, and last night trying to install Perl in Vista about landed my new laptop in the river out my front door!

So, I just need to install it, huh? And go from there? It looks like everything works from running it from the cd - I haven't had any weird issues besides the wireless and the sound. I checked the forums for my particular brand of laptop and haven't seen any issues besides those two, and although I don't understand how they got fixed, so it looks like I'm good to go.

---

### Post by tamara_meske on 2007-05-06
> **rygar said:**
> if you can log on to your router through Windows, you can check what security protocol your network uses.
I did this, and it's WEP, and it does just like you said - it never connects. Oh well - I'll connect via ethernet at starman's suggestion until I can get the details worked out.
Thanks again!

---

### Post by tact on 2007-05-06
Hi Tamara,

your 10 digit number for the wifi is very likely a 64/128 bit hex key.   when connecting and entering the key make sure to set that type properly.  then u will be connected.  can connect while using LiveCD no problem.  Make sure it works from the LiveCD before you install.

---

### Post by nubutu on 2007-05-06
Something else you can do is changing the settings of your modem for testing purposes. It seems you shouldn't have any problem in connecting, but I did it this way when first installed Ubuntu, as there are some issues with wireless networking that can be tricky if you're not familiar with them--and this is not, by any means, unique of linux, I've seen it happening so many times to Windows' users. 

So, in case you don't know, the usual way to modify your modem configuration is to open an internet browser (Internet Explorer will do it) and type in the address tab: 192.168.1.1, which should be your modem's IP. Once there it'll ask you for a username and a password, usually defaulted to something like "admin" and "admin", but this varies and you're better off reading the manual to make sure. Now, what I advice you is to leave your security settings plain opened: no hidden SSID, no encryption key, MAC filtering whatsoever. This way, if you don't get connected, you can start thinking of a driver problem. 

Once up and running, you can go back and customize the settings the way you like them. Make sure you enter the key for whatever protection you set up in the right way, this is, if you set up a password in ASCII when playing with the router, do not type that string as hexadecimal in Ubuntu's network utility...

By the way, wise words those about wireless security, although I don't think any protection is, as of today, taught enough to stop somebody really keen in breaking it.

Have a lot of fun

---

