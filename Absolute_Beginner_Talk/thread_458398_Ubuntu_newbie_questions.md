---
title: "Ubuntu newbie questions"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by mistersee on 2007-05-29
I am from a microsoft background and new to linux so I have a few questions to post to anyone who can point me in the right direction for best practices when using ubuntu.

1. when using windows you need to have a firewall installed, is this the case with ubuntu? if so whats best?
2. the same goes for an antivirus? 
 
any help is greatly appreciated.

Thanks

ubuntu newbie

---

### Post by meng on 2007-05-29
This was asked a very short while ago!
[http://ubuntuforums.org/showthread.php?t=458354](http://ubuntuforums.org/showthread.php?t=458354)

---

### Post by starcraft.man on 2007-05-29
Ubuntu has its own firewall installed by default, it is called IP tables. It works very well, unless you need to port forward, leave it as is and don't worry about it. That said, the best firewall any computer can ever have is a NAT router, because of the fact that network traffic gets stopped and dropped off at the router if its not requested (thus, making you invisible on the net). Routers of course cost money, thats your choice. IPtables is good enough as a firewall.

No AV is needed for linux, I'd go into detail as to why that is, but its easier to point you [here.]("http://www.psychocats.net/ubuntu/security") The only reason to install an AV is if you forward email to people (you can then scan attachments to make sure their clean for window users you forward to). If you don't download/forward email, don't worry about it at all.

Edit: Ha, meng beat me >.>.

---

### Post by lsalminen on 2007-05-29
I don't find either of these neccesary, and unless you are accessing a large number of adult websites or illegal websites, I don't think you'll have any trouble. :)

---

### Post by meng on 2007-05-29
> **starcraft.man said:**
> Ha, meng beat me >.>.
I just took the lazy option!

---

### Post by marco123 on 2007-05-29
Never had any problems even with adult/torrent sites with the standard Ubuntu install.

Once a javascript closed the browser and said that my registry needed cleaning!  I just laughed.:D

---

### Post by meng on 2007-05-29
> **marco123 said:**
> Never had any problems even with adult/torrent sites with the standard Ubuntu install.
Once a javascript closed the browser and said that my registry needed cleaning!  I just laughed.:D
Maybe your computer needed cleaning ... you know ... adult sites ... interesting stains ...

---

### Post by marco123 on 2007-05-29
> **meng said:**
> Maybe your computer needed cleaning ... you know ... adult sites ... interesting stains ...

lol. 

 I was worried for a second but then realized Linux has no registry.  I use the noscript extension for firefox now so I don't even get any of those popups anymore. :)

---

### Post by mistersee on 2007-05-29
Thanks everyone for your advice, it seems strange for someone like myself who has eat and slept windows for so long not needing to install a firewall or av, I guess this is something I will need to to get used to a long with other things in ubuntu.

anyway thanks again.

:p

---

### Post by DJ Wings on 2007-05-29
[FireStarter](http://www.fs-security.com/)
An easy-to-use GUI firewall.

---

### Post by marco123 on 2007-05-29
Don't forget that Linux was built for networking unlike windows, and that Ubuntu ships with no open ports.  So there's nothing to connect to for hackers.

---

