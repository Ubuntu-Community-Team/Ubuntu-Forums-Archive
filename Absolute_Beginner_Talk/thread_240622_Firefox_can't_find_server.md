---
title: "Firefox can't find server"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by rabosajr on 2006-08-21
I have just installed Ubuntu 6.06 but when I launch Firefox I get "server not found" message most of the time. I am able to access yahoo.com occasionally and was able to do some search but most of the time I get "server not found" message from the site as well as the other sites.
When I tried to use Update Manager, all downloads failed.
I use a dial-up modem on my PC with WInXP and my Ubuntu PC is wired to it.
Need help here, thanks.

---

### Post by drtvasudevan on 2006-08-21
have you configured your modem to dial up?
open teerminal and type

To configure dialup 
> sudo pppconfig

To connect dialup 
> sudo pon provider_name

To disconnect dialup 
> sudo poff

---

### Post by rabosajr on 2006-08-21
> have you configured your modem to dial up?
I'm a little confused here. Do I have to configure the modem when it is installed on another PC running on Win XP? And firefox works just fine on this PC.
It is on another PC running on Ubuntu that I'm having problems with firefox.
There seems to be no problem with networking coz I can ping both PC's.
Thanks.

---

### Post by drtvasudevan on 2006-08-21
yes, you need to configure.
next is to disable the ipv6 stuff.

---

### Post by jamadagni on 2006-08-21
For that what you do is:

1. Type about:config in the address bar and press Enter. You should see a list of Firefox settings.
2. Type v6 in the filter field. The filtered list should now display a setting called network.dns.disableIPv6 which is set to false
3. Double click the setting to change it to true.

Now your net access should be ok. If the setting is true, and you are still not able to access the net, then some other cause and solution should be found.

---

### Post by drtvasudevan on 2006-08-22
> **rabosajr said:**
> I'm a little confused here. Do I have to configure the modem when it is installed on another PC running on Win XP? And firefox works just fine on this PC.
It is on another PC running on Ubuntu that I'm having problems with firefox.
There seems to be no problem with networking coz I can ping both PC's.
Thanks.

you mean you have 2 pc and networked them and want to share the internet connection?
if the network is already set up and working the problem is with firefox and the ipv6 tweak should set it right.

---

### Post by rabosajr on 2006-08-22
> you mean you have 2 pc and networked them and want to share the internet connection?
if the network is already set up and working the problem is with firefox and the ipv6 tweak should set it right.
Yes, that is the situation. But even before I did the ipv6 tweak I am sometimes able to access a site but most of time I get the "can't find server" message.
Additionally, if I use the update manager, the update fails all the time.
The tweak did not solve my problem.
The internet sharing seems to be okay coz using another PC (Ubuntu 5.10) i do not encounter the same problems with the internet connection sharing.

Thanks.

---

### Post by drtvasudevan on 2006-08-22
sorry i am unable to help as i dont know anything about inter pc networking.

---

### Post by mr2cool on 2006-08-22
hey if you are runing dhcp and are behind a router then make sure in dsl settup on your card that u have entered a username and password to your isp provider...i couldnt get internet until i added mine take a tick out of box beside the password

---

### Post by rabosajr on 2006-08-31
Everything seems to be fine now. :razz: 
I think the problem was with the DNS Servers. I'm using Static Address and set DNS to 210.14.16.5 and 210.14.16.2
I have not having the problems for 3 days now.
Thanks for the replies.

---

### Post by toasted on 2006-08-31
oops sorry  :D

---

