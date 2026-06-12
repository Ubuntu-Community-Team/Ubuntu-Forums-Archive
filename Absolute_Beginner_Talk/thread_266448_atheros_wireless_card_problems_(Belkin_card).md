---
title: "atheros wireless card problems (Belkin card)"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by shamu on 2006-09-27
I've had ubuntu on my system for about a week and love it, except for my wireless card just isn't working properly with ubuntu.  Ubuntu can see wireless networks in range, but I cannot conect to any (even those that I should be able to or can on the windows side partition).  Have been having trouble with ndiswrapper and madwifi, tried modprobe but I'm not sure if I'm skilled enough for that one yet.

I know there are a lot of posts about this stuff but none have seemed to work for my problem.  Any suggestions? 386 kernel.

---

### Post by deadgobby on 2006-09-27
> **shamu said:**
> I've had ubuntu on my system for about a week and love it, except for my wireless card just isn't working properly with ubuntu.  Ubuntu can see wireless networks in range, but I cannot conect to any (even those that I should be able to or can on the windows side partition).  Have been having trouble with ndiswrapper and madwifi, tried modprobe but I'm not sure if I'm skilled enough for that one yet.

I know there are a lot of posts about this stuff but none have seemed to work for my problem.  Any suggestions? 386 kernel.
 wireless cards and Linux/Unix can be a pain is the arss. So I give you a link off of Ubie wiki site.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Find the card you have and see if you can get it running

---

### Post by shamu on 2006-09-28
Thanks for the advice.  Checked out the list (my card is Belkin F5D7010) and it said my card used a broadcom chipset but when I type lspci in a terminal it says

"Atheros Communications, Inc.: Unknown device" (...)

right after Network Controller.  Should I still use the broadcom wiki or try something else?

---

### Post by shamu on 2006-09-28
Here's something wierd.  My card connects to the internet, and ubu recognizes this, but i can't ping any websites.  signal strength fluctauting around 85%.  any ideas?

---

