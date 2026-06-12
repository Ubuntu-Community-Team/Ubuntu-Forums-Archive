---
title: "Internet user authentication woes!!!"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by ijwilliams1975 on 2006-01-26
I am currently planning a small wireless network in halls of residence that will allow subscribers to connect to the internet via my wireless router.
What I would like to find out is how to set up: -
a facility that when a user tries to connect to the internet, if they have not logged in, have them diverted to a login page requesting usernames and passwords

a means to add and remove internet user names passwords and log access

I have just moved over to linux from MS and to be honest i dont know where to start!

My setup is a linksys wrt 54g wireless router with brain slayers ddwrt firmware connected to my DSL modem - all working ok for normal browsing
Ubuntu breezy 5.10 with the i686 kernel on a 3ghz intel processor with 512mb ram
i also have a 12 port unmanged switch...

ideally the process should go as follows:- user connects to access point - get diverted to internet login page... autheticates and browses or doesnt and gets a snotty message!
if any one can help it would be greatly appreciated!!!!!!
Many thanks,
Ian

ps. if I get somewhere with this I will create a step by step how-to guide!!!... google didnt turn much up..

---

### Post by mips on 2006-01-26
I think you are looking for Squid Web Proxy Cache, [http://www.squid-cache.org/](http://www.squid-cache.org/)

You can install it via Synaptic or Adept.

You might also want to use a linux box as a router,firewall,dhcp,dns server - [http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by ijwilliams1975 on 2006-01-26
errr.... ok used synaptic to get the packages...ummm...any ideas on how to set it up??... im errr duuur... baffled lol... had a look at the docs and to be honest there is an awful lot of of info!.... do i need to configure apache for the authetication side of things??... to be honest im not to gemmed up on the linux side of life.. infact... if I was a frog..it would be like migrating from catching flies to catching lunar modules lol... any help with this would be really really appreciated! essentially, we only have one bradband connection in our accomodation so it would be really nice to share it out but with authentication... im looking at both windows and linux web clients, ... i reaaaaaly reaaaly dont want to go down the microsoft route to do it!...  :-) ubuntu has so far proven to excell in a number of areas over XP in firewire support for DV editing, application availablilty, community ethos and overall stability... plus if I get this one cracked I might try and put some scripts together for download for generic configuration..

---

### Post by mips on 2006-01-26
I have never used squid in my life but it seems to be the package to use from what I hear.

I wil have a look at it tomorrow or the weekend and let you know if I abosrbed anything. Bit late here to focus on docs&manuals now :shock:

---

### Post by mips on 2006-01-26
Google "squid GUI"

[http://www.squid-cache.org/related-software.html](http://www.squid-cache.org/related-software.html)
[http://www.swelltech.com/briefs/webmin/squid.html](http://www.swelltech.com/briefs/webmin/squid.html)    access via webmin [http://www.webmin.com/](http://www.webmin.com/) available via synaptic

---

### Post by DeadEnd on 2006-01-26
Well I would look at chillispot and NoCatSplash as possible solution esp if your running dd-wrt firmware

---

### Post by crobruncato on 2006-03-04
Look at zonecd [www.publicip.net](www.publicip.net). Easy to use, should do what you are looking for. Free also, although there are premium packages. It is dependent on thier servers, so if they go out of business or decide to change the way they work, it could cause problems.

Rob

---

