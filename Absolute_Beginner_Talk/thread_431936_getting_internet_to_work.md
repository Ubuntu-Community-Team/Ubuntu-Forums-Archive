---
title: "getting internet to work"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by thedatahouse@yahoo.ca on 2007-05-03
Newbie for sure: Internet connectivity at home is done thru my ISP using DSL and their wireless router. I just got rid of XP on my DELL desktop and successfully installed 7.04 with no problems. I do believe I chose to set up the network manually later though. Hence now i am trying to  access the internet but of course its not working.  Hence I am thinking my Compact Wireless-G USB Adapter from Linksys Model #  WUSB54GC  may be the problem. If i view the hardware from the terminal line it does seem to be there but I don't see it in my network connections. Any idea on how to further troubleshoot. Missing a driver perhaps? thanks in advance

---

### Post by starcraft.man on 2007-05-03
> **thedatahouse@yahoo.ca said:**
> Newbie for sure: Internet connectivity at home is done thru my ISP using DSL and their wireless router. I just got rid of XP on my DELL desktop and successfully installed 7.04 with no problems. I do believe I chose to set up the network manually later though. Hence now i am trying to  access the internet but of course its not working.  Hence I am thinking my Compact Wireless-G USB Adapter from Linksys Model #  WUSB54GC  may be the problem. If i view the hardware from the terminal line it does seem to be there but I don't see it in my network connections. Any idea on how to further troubleshoot. Missing a driver perhaps? thanks in advance

Ummm, just a first up suggestion, do you have an ethernet line to plug into this till we find a permanent solution? That would be the quickest way to get on internet, network manager should automatically configure it.

I personally don't know if there is any way to get one of those USB wireless cards working with Ubuntu. My best guess however, is for you to look at the NDISwrapper project, look for your card in the hardware list and see if its supported. [Link.]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/")

---

### Post by thedatahouse@yahoo.ca on 2007-05-03
thanks looks like I'll keep it hard wired then. the linksys wireless is not even listed in the NDISwrapper project listing. Thought it was a popular one. Thanks for your reply. ciao

---

### Post by croxi on 2007-05-03
I have had similar problems to you with DSL connection problems and continue to have them up to today. I have tried to use Thunderbird2 as a backup but it also won't connect to the email servers. 

it continues to tell me that I have a broken pipe. 

I am hopeful that someone will come up with a fix for this problem soon

---

