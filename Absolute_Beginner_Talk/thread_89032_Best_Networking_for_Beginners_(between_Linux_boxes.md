---
title: "Best Networking for Beginners (between Linux boxes?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Herman on 2005-11-11
What is the easiest way for Ubuntu newbies to get networking going _between two or more Ubuntu boxes?_
If they are dual booting they can already use their Windows Network when they are booted into that, and they can mount their Windows filesystem in Ubuntu, and they can access thier Windows computers already from Ubuntu with the Windows Network. (Just not the other way around). 
If they use the Automatix automatic graphical installer and tweaker tool they'll have '8)gftp client for gnome with ssh capability.' Would that be the easiest/fastest/safest path for newbies to get them up and running quickly?
Would Samba be easy enough for newbies and is it secure?
(In the recent firewall debate  I was shocked that some people's machines did't pass the firewall testing at 'Sheilds Up!', and 'Sygate Security Services', which any Ubuntu computer should pass as 100% stealth if it hasn't been tampered with.)
I like SSH and I'm wondering what others think, I am I the only one? Or is SSH popular but doesn't get mentioned much on the forums?
Are there easier/better/safer alternatives? :confused:

---

### Post by apjone on 2005-11-11
I like ssh, its secure and easy to use. i use it at home and work. best off configuring the network manually and asign static IP address , edit /etc/hosts and hostname. also edit /etc/resolv.conf for your dns. sounds alot of work but most can just be copied str8 to each machine,

---

### Post by Herman on 2005-11-11
> asign static IP address , edit /etc/hosts and hostname. also edit /etc/resolv.conf for your dns. sounds alot of work
I see, I didn't know before that people might need to do those things, I have a router which assigns my IP addresses automatically.  So I might have a mistaken impression. It was easy for me, but might  be a little more work for others depending on their hardware. Thanks! :smile:

---

### Post by apjone on 2005-11-11
i also have dhcp but because i run service's on my linux box's i just find static easier to work with

---

### Post by Herman on 2005-11-11
> i also have dhcp but because i run service's on my linux box's i just find static easier to work with I imagine someone who wanted to set up Samba would still need to do the same thing, if they want or need to use static IP addressing with that too. It still might not be a mark against SSH.

---

### Post by apjone on 2005-11-11
yeah , any service like i would use static , depends on the routers dns compatibility on the lan. stick with static eg 192.168.1.* = windows 192.168.2.* = linux . or whatever

---

### Post by Herman on 2005-11-11
It seems to me that my router's giving out of IP addresses can cause SSH to work erratically now that you have pointed that out to me. I suppose that might depend on the sequence in which the computers are started up each morning. Some days it would cause trouble and some days not, or sometimes only between some computers. How did you assign the static IP addresses, please, apjone?

---

### Post by Herman on 2005-11-11
Well, I'd like to let you know, apjone, that you have helped me immensely by bringing the IP-from-the-router issue to my attention. It had not occurred to me that before, because most mornings our computers get started up in the same sequence anyway. It does explain why some days SSH has been working better than others. (Of course!). I had a couple of our computers that would only connect one way. I have solved that problem now from your clue about the IP addressing. It seems I must have connected these two computers one day in the past on a bad morning when our computers were started up out of sequence. This has caused the 'known_hosts' file in the .ssh directory, in the user's directory to have in incorrect ID for that IP address. I simply opened it with gedit and deleted the entire entry for that IP and closed everything and re-tried the connection. The connections I was having problems with went through as new connections then.
From now on as long as I start the computers up in the same sequence I'll have 100% SSH connectability all over my LAN!:D 
Thank You apjone, I have learned something from you which has made me very happy!:p

---

