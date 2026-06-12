---
title: "Compaq nx9010 ???????"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-04-09
I have just installed Ubuntu on to a Compaq nx9010 laptop, everything seemed to be fine till I decided to log onto Ubuntu forums.  I cannot get on the internet.  The laptop has a wireless nic card inside and I see that it is talking to my wireless router but when I try to get on the internet it won't let me (i typed ubuntu.com and said it could not be found and I tried google to and had the same response).  When i went to the command prompt and typed iwconfig the response was that lo etho and eth1 had no wireless extensions, but when I go to my desk and see two small network computers blinking (i clicked on them) and I get a screen that says Connection Properties, and that I am using lo and status is idle.  I also see packets being set and received.  Am I missing something?](*,)

---

### Post by karthik085 on 2006-04-09
I believe your eth1 is your wireless connection. 

If you are using your wireless card, are you able to ping to your wireless router? (ping <wireless router ip address>)
Do you get an valid IP address? (command: ifconfig)
If so, can you ping to a website like Google.

---

### Post by NeoGreen on 2006-04-09
Tried ifconfig and no address, I also tried pinging my router and it told me it was unreachable

---

### Post by karthik085 on 2006-04-09
You have not set your wireless connection properly. How did you set it up? Did you follow any guides/posts to do?

---

### Post by NeoGreen on 2006-04-09
I actually didn't set anything up, I assumed seeing the two small icon network computers on my desktop that told me that they were setup.  Where or how do I set up my wireless nic card to my wireless network?](*,)

---

### Post by karthik085 on 2006-04-09
There are different wikis/guides for different chipsets. Depends on what wireless card you are using. For example, if you are using Broadcom chipset, you can use this wiki:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)
[http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+network+manager](http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+network+manager)

Also different methods, ndiswrapper, network manager, ....
So, based on your chipset, search on forums, wiki, guides...

---

### Post by NeoGreen on 2006-04-09
Thanks I'll look them up:D

---

### Post by NeoGreen on 2006-04-23
I got it!!!!!!!! It's working now, thanks :) :p :) :p :)

---

### Post by pelatrix on 2007-12-01
It would be great if you can tell me how you did it... If you remember, of course.. ;) Thanks in advance...

---

### Post by idcolvin on 2007-12-14
Hi,
I'd love some help setting up my nx9010 to use wireless. Does anyone have an easy guide for making it work with 7.10?
Many thanks in advance.
Ian

---

