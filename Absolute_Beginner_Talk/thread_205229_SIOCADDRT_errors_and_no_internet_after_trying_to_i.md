---
title: "SIOCADDRT errors and no internet after trying to install eciadsl"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-06-28
Hi all,

this appears to be a Dapper issue as it has come up without an answer here [http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=3187&highlight=siocaddrt]("http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=3187&highlight=siocaddrt"). 

I have been trying to install the eciadsl driver and came up with the following error :

>connection successful 
>
>eciadsl 5/5 - setting up route table... 
>
>waiting for ppp0 
>adding default route... SIOCADDRT: file exist 
>failed to set default route to ppp0" 


At some time between starting to install the eciadsl driver and the error above, I have lost internet access to the internet through my Win2K laptop.

When I ping my modem, I get "connect: Network is unreachable"
When I run ifconfig I get no error
When I run route -n I get no data at all.
If I try to add a default route, I get "Network is unreachable"
My eth0 is enabled using DHCP.

What can I do to get back access to the internet through my laptop?
What can I do to get the eciadsl driver working?
Does anyone have eciadsl working with Dapper?

Thanks in advance for your help,

Adam.

---

