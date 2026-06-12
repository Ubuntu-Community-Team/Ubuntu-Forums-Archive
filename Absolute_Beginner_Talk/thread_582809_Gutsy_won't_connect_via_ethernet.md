---
title: "Gutsy won't connect via ethernet"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Andy Norfolk on 2007-10-20
I'm a tad teasy about this! I've had Feisty running well for months and it did "just work" when I installed it.

The same is not true about Gutsy! I've tried upgrading on-line Feisty twice and an install from disk twice. It simply refuses to work with my modem. What is really annoying is that it uses the same modem to update itself and then screws up. I have tried unchecking roaming mode and looked at other setting with no success. What is really annoying is that this version of Ubuntu uses the same modem to update itself and then glitches the connection. 

Meanwhile on the same computer I have MInt Celena, Opensuse 10.3 and XP all of which still connect with no problem. Gutsy does not "just work".

So - um - help - anyone got any suggestions?

Andy N

---

### Post by apatris on 2007-10-20
If you are connecting via ethernet then the modem is not the problem. I  seem to be having the same problem and can't figure out why. I does function properly in the local network though and it seems that it can use some ports. For example amsn connects normally. I suspect it has something to do with DNS.

update: I just pinged 216.239.59.104 (google's ip address) and it works but it won't load any websites  or download mail via pop. It's got to be something related to DNS

update2: I have put my isp's dns servers adresses instead of letting the router do it and it now works. You need to find out your isp's DNS go to "manual configuration" click on the DNS tab and put the 2 DNS server addresses.

update3: It seems to be "losing" the DNS settings after a while and after a reboot. Might be a bug.

**Resolved!** It seems that some routers (like the one I have) cause linux to think they are dns servers. I don't know why it was not problem before but the following links resolve it.

[http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/](http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/)    ( this is to disable ipv6 if you don't need it, it will make browsing faster

[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)              ( This tells ubuntu to use the particular servers no matter what, and in this case the opendns ones

---

