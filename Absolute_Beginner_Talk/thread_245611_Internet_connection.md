---
title: "Internet connection???"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by gogreenpower on 2006-08-28
im very new to linux and just installed ubuntu onto my laptop, all went well and i had a play around and then decided to get on the net. for the life of me i cant figure out how to do it, i have been through the help forums and tried what they recommend but no luck, i have a lan and wireless connection to my router and use pppoe. i have tried "sudo pppoeconf" 

but i get the reply 

"sorry, i scanned 2 interfaces, but the access concentrator of your provider did not respond, please check your network and modem cables. another reason for scan failure may also be another running pppoe process which controls the modem"

the comand "dpkg -s pppoeconf"

gets "install ok installed"

and thats about where the help ends and my brain stops any ideas would be much appricated.



green.

---

### Post by handy on 2006-08-28
Can you connect via network cable?

If nothing else, this will give you a bumb! :KS

---

### Post by gogreenpower on 2006-08-28
after alot of fiddling around i managed to get on the net however only for about five minutes at a time. in the networking window on the DNS tab it has the IP address of my router 10.1.1.1which i change to the preferred DNS setting of my router 202.43.226.12 which works and i can get on the net but within 5 minutes or so i get the cannot connect pages and when i check the networking tabs again it has gone back to 10.1.1.1, i change it back and the net works again but this happens everytime????


green

---

### Post by handy on 2006-08-28
I have had a problem with my router & Ubuntu since I started using Ubuntu:

I can use the web (after turning off ipv6) but I can't access repositories?  I found a [work around (eventually) in Breezy]("http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router"). 
In Dapper the above workaround is not possible. I found that I only have to put in my ISP's DNS addresses (1 would do) at the **Menu: *System / Administration / Networking - DNS tab*.**

Which is the same as putting them in the **/etc/resolv.conf** file.

I get better than 5 minutes by a mile.  But sometimes I have to put the DNS addresses back in after each reboot!!! Only if I want repo's though.

This seems to be an incompatability between Ubuntu & some routers (chipsets?), I have hatched a plan that I am about to attempt to put into action, where on every reboot I will use **Menu: *System / Preferences / Session - Startup Programs***  to **copy /etc/resolve.conf  /etc/resolv.conf** which will have the effect of putting my correct DNS addresses in place every time I boot up.  Which is still really no help to you is it...

Someone here will solve it for you for sure.  I have at least bumbed you again... :rolleyes:

---

### Post by handy on 2006-08-29
I have added the solution to **my** problem in [another thread]("http://ubuntuforums.org/showthread.php?t=241110") post #15. The only way that it could help you, is you could have an icon on the panel that you could hit & it would run a tiny script that would put the correct DNS address back for you...

Not much help am I? LOL sorry best I can do for you, apart from the bumb that is!

All the best :KS

---

### Post by CameronCalver on 2006-08-29
I used to have that probelm also but i fixed it with ```
gedit /etc/resolv.conf
``` and i know that is the same as editing it in the DNS tab but for some reason it worked but i think handy's point about the script would be a good idea and i have done a bit of scripting but i am unsure if it is even possible to open a file put something in it and then save it?

---

