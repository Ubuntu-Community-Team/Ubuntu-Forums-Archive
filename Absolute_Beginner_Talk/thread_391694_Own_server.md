---
title: "Own server"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by depablo on 2007-03-23
Sorry if this has been asked already, it probably has as this forum is huge.

Been looking at forums and disk usage, cost of web space. Would I be able to run my own server with just the ubuntu and lamp from your download section?

Is there anything else I would require regarding security and accessing the network 24/7 apart from a domain name and static IP?

If it has been asked before sorry, a link to the relevant topic would do.

TIA

---

### Post by jeffathehutt on 2007-03-23
Technically, yes, you can run your own server with Ubuntu and the lamp programs.  You can install firestarter to configure your firewall as needed.

Keep in mind, however, running a server on your home pc may violate your ISP's policies.  Make sure you read their policies to determine if it is legal for you to run a server from your home.  Also, to make it easier on yourself, your ISP would have to give you a static IP.

---

### Post by christhemonkey on 2007-03-23
And if you dont have a static ip adress you can always use a free service like dyndns.com to still have your own server.

It is very possible, and many people are in fact doing this on their ubuntu boxes.

---

### Post by depablo on 2007-03-23
Thanks very much for the prompt replies, is security a real issue as the setup appears simple enough?

TIA

---

### Post by christhemonkey on 2007-03-23
As ever security should be in mind when setting up the server, but by default the LAMP stack should be quite secure.

Setting it up is simple use a guide like this if you feel you need one:
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

### Post by depablo on 2007-03-23
Thanks to all for the excellent replies, more than enough to be going on with.

regards
depablo

---

### Post by nhandler on 2007-03-23
The servers are very secure. However, your pages can make your site vulnerable. If you are only dealing with static html pages, you can ignore the rest of this post. If you are dealing with scripts like php and perl (and whatever else), you might make your site insecure. Take for example a file manager script. If you code it yourself, someone could probably exploit it to allow them to view all the files on your pc. You have to be very careful with these kinds of scripts.

---

### Post by depablo on 2007-03-24
Cheater

Thanks for the warning, will only have basic html siite with a forum, the forum script will be updated as required.

(probably phpbb or yabb2)

Once again
thanks to all who respoded

---

