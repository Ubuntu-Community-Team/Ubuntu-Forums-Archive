---
title: "Connecting Desktop to Wireless Network..."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by DoctorIngenious on 2008-01-30
Hello, 

I'm new to Ubuntu and need help configuring my Desktop to connect wirelessly to my home network. Let me start with what I have:

Linksys Wireless-G Cable Gateway WCG00v2-CC
Linksys Wireless-G USB Network Adapter
Ubuntu 7.1

So when I plugged in my USB network adapter it was immediately recognized and was able to see the surrounding networks with it, including my own home network. When I go to connect to the network it of course asks me what Wireless Security I want to connect as including the respective passphrase/key as well as the Authentication type. 

I've tried both connecting via WEP 128-bit Passphrase/Phasphrase as well as with WEP 64/128-bit Hex w/key but neither connected succesfully (window comes back and asks for key again). I logged into my router and confirmed the passphrase and key were correct. I believe I want Shared Key for Authentication type in both cases.

Sometimes when I go to Login to the Network I get one green dot (what do the dots mean?) but not the other, not sure if that means anything...

Thanks for all of the help. Kind of going crazy over this.

---

### Post by eolson on 2008-01-30
I'm trying to remember what the laptop setting are on my laptop ....  I seem to remember that it was pretty much as you say except it wanted to be something like   "open."   Wish I had it handy to confirm that.  Also,  after everything else was set up it seemed to want to be set to "roaming mode."

Sorry I can't be more specific.  I'm here and the laptop is there.

---

### Post by bwhite82 on 2008-01-30
It seems that you are not using the correct 'algorithm' to connect. Verify what yours is set to in your wireless router. Goto: Wireless tab>Wireless Security tab and verify that both the security 'mode' and 'algorithm' match when you try to connect in Ubuntu. For my router, I use WPA Personal and TKIP for the algorithm.

---

