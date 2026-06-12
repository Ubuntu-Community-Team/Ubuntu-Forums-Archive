---
title: "wireless router"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Geir102 on 2007-10-26
Hi this is not realy a ubuntu question but found this the best palce to ask.

Im running a SSH server on a ubuntu box, whict i connected whit a kabel to the router its ip is 192.168.1.104. But when i connect whit my laptop to the wireless, i cant connect to this server. It works if im connect tru a wire. The router is WRT300N.

Any one know whats wrong?

---

### Post by Austin_KW on 2007-10-26
I dont know this router, but the it sounds like wireless isolation is turned on. Check the wireless (security) settings on the router.

---

### Post by sailor2001 on 2007-10-26
system/admin/network  click on wireless/properties. If your roaming is ticked, untick and give it automatic config. and the network name is?

---

### Post by Geir102 on 2007-10-28
Ap isolation is not on. Alle the computers connected wireless can assess ecaother. Its like there is one nettwork for wireless and one for wierd. Its strange

---

### Post by Austin_KW on 2007-10-28
> **Geir102 said:**
> Ap isolation is not on. Alle the computers connected wireless can assess ecaother. Its like there is one nettwork for wireless and one for wierd. Its strange

Odd, sounds like the wireless LAN is not bridged to the wired LAN. Is there any options for enabling bridging or broadcasts.

---

### Post by Geir102 on 2007-10-28
No cant find any thing. There are a lott of options but nothing looks like it will do this.


this is the speks by the way
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1144763513404&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1144763513404&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by Austin_KW on 2007-10-28
Look on the site for any firmware upgrades.

---

### Post by Geir102 on 2007-10-28
Its whit the newest firmware:-(

---

