---
title: "is there anywhere i canget other help?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by larrypinsupplync@msn.com on 2006-03-22
I would really like to be able to use Ubuntu but I can't find th help I need here. I'm still using wincrap xp to post this and would just like to at least configure my internet connection so that i can actually use it to see something other than the default home page. PLEASE HELP!:confused:

---

### Post by aysiu on 2006-03-22
You posted an hour ago. Seriously. Can you at least wait?
Or can you provide more details in your original post?

---

### Post by larrypinsupplync@msn.com on 2006-03-22
I asked for help not sarcasm.

---

### Post by Brunellus on 2006-03-22
[QUOTE=larrypinsupplync@msn.com]I asked for help not sarcasm.[/QUOTE]
and we're asking for information, not churlishness.

The simple fact that you are in distress is not enough:  we need to know what's the matter, and what your hardware is.

---

### Post by aysiu on 2006-03-22
[QUOTE=larrypinsupplync@msn.com]I asked for help not sarcasm.[/QUOTE] I'm not being sarcastic--I'm being sincere. If you make a post, don't complain if it doesn't get answered within an hour. Be patient.

Everyone here is a user, just like you. We are not paid support. We are not Canonical employees. I'd help you myself if I knew anything about setting up internet connections. Unfortunately, Ubuntu auto-detected my ethernet connection, so I don't really know much about fixing stuff like that.

Be patient.

---

### Post by petervk on 2006-03-22
Post more information or no one can help you. 

What kind of Internet connection do you have? Hopefully you have some sort of a high-speed link through a Ethernet cable. If so, tell us and what you've tried.

If it's dial up this is a good guide: [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")
But don't expect too much. Dial-up support in Ubuntu is ok as long as you have a supported modem, if you don't there's not much anyone can do. 

You'll probably have the greatest success if you can get access to another computer with a working Internet connection to read the guides on while working on the Ubuntu computer.

Oh, and be glad people even responded to your post. If your ungrateful and rude, don't expect much sympathy.

---

### Post by NeghVar on 2006-03-22
You may not have been sarcastic here, but one of your other posts is pure sarcasm. Like they said, we need more information to even begin to have an idea of what is wrong.

---

### Post by larrypinsupplync@msn.com on 2006-03-22
I stated earlier that i had very little knowledge of how this stuff works.
I need to know what info you need. someone asked what kind of connection i had . I replied DSL and I havent gotten a response. I can tell you anything you need to know about my hardware. Intel Mobo D845GLLY with P4 1.5.Onboard LAN.

---

### Post by aysiu on 2006-03-22
What happens when you go to System > Administration > Networking? Can you post a little screenshot of what pops up after you enter your password?

---

### Post by brandoncolorado on 2006-03-22
Doctor my body hurts.

---

### Post by larrypinsupplync@msn.com on 2006-03-22
the network settings open. eth0 is showing active. set to: dhcp. I have also typed in the address to starbridge, my modem manufacturer, which is 192.168.1.1 in the browser, and it takes me to the site so i know its connected. I just cant acess any other page.

---

### Post by larrypinsupplync@msn.com on 2006-03-22
[QUOTE=brandoncolorado]Doctor my body hurts.[/QUOTE]
i told you i dont know ANYTHING about this. i gave you the problem in myearlier post beyond that you'll have to tell me what info to give you.

Doctor: WHERE DOES IT HURT?

---

### Post by aysiu on 2006-03-22
[QUOTE=larrypinsupplync@msn.com]the network settings open. eth0 is showing active. set to: dhcp. I have also typed in the address to starbridge, my modem manufacturer, which is 192.168.1.1 in the browser, and it takes me to the site so i know its connected. I just cant acess any other page.[/QUOTE] Does it look something like this? This is my configuration--what I had out-of-the-box, and it works with my DSL connection (which is through a router, by the way).

---

### Post by larrypinsupplync@msn.com on 2006-03-23
[QUOTE=aysiu]Does it look something like this? This is my configuration--what I had out-of-the-box, and it works with my DSL connection (which is through a router, by the way).[/QUOTE]
yes it looks exactly like that

---

### Post by Iowan on 2006-03-23
[QUOTE=larrypinsupplync@msn.com]... I have also typed in the address to starbridge, my modem manufacturer, which is 192.168.1.1 in the browser, and it takes me to the site so i know its connected. I just cant acess any other page.[/QUOTE] Does 192.168.1.1 actually connect to a website - or is it an HTML page stored on the modem?  I don't have DSL, so I'm unsure if that address gets converted to a REAL IP Address at the modem, or if it's enough to get to the ISP.

---

### Post by Brunellus on 2006-03-23
192.168.1.1 is in the block of IP addresses reserved for private networks, so what you're seeing is a webpage being served up by your modem.  

The good news:  your network interface (eth0) works.

Next step is to configure PPP over Ethernet, which is the means by which you actually connect to the internet.  As I don't connect that way, and never have, I'll leave that to the other ADSL users to tell you about.

---

### Post by larrypinsupplync@msn.com on 2006-03-23
[QUOTE=Brunellus]192.168.1.1 is in the block of IP addresses reserved for private networks, so what you're seeing is a webpage being served up by your modem.  

The good news:  your network interface (eth0) works.

Next step is to configure PPP over Ethernet, which is the means by which you actually connect to the internet.  As I don't connect that way, and never have, I'll leave that to the other ADSL users to tell you about.[/QUOTE]
Keep it comming guys

---

### Post by larrypinsupplync@msn.com on 2006-03-23
what is the DNS? ow do I know what to set it to?

---

### Post by Iowan on 2006-03-23
[QUOTE=larrypinsupplync@msn.com]what is the DNS? ow do I know what to set it to?[/QUOTE]DNS is Domain Name Service  It's how a name (like ubuntuforums.org) gets converted into an IP address. Again... not a DSL or ADSL user... but I presume your ISP has a DNS server.  That information should be available on the machine you're currently using.  [http://ubuntuguide.org/#activatedeactivatenetworkconnections]("http://ubuntuguide.org/#activatedeactivatenetworkconnections")   Some reading for you.

---

### Post by Magrioteli on 2006-03-23
[QUOTE=larrypinsupplync@msn.com]I would really like to be able to use Ubuntu but I can't find th help I need here. I'm still using wincrap xp to post this and would just like to at least configure my internet connection so that i can actually use it to see something other than the default home page. PLEASE HELP!:confused:[/QUOTE]

Yo! 


If you still are running XP, go to the CMD (START/RUN and type cmd) and hit enter as hard as you can :-D 
When you are in type: config /all   (blank between config and /)
There are all the information you need about your IP address, DNS and so on. 

But do you really have to report  this info to connect? Didn't you use DSL? I have  DSL via the telephone line, and my IP address isn't static. And it worked from start. 

As Brunellus wrote the IP address you've stated are for local networks - and it won't get you out on  the Internet cloud. 

Good luck.

---

