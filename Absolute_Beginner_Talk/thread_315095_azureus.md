---
title: "azureus"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-12-08
ok, i went to isohunt.com, and got 3 .torrents. i opend them with azureus, but it seems like the download speed is going to slowly. its goin at 30kbs with over 200 seeders. And it says im behind a firewall (unless ubuntu automatically comes with one, im not). and it says i have a NAT problem, wich i have no idea what the means. could somebody tell me if this is average, or is mine screwed up, if so, how do i fix it?

---

### Post by mahy on 2006-12-08
> **Cardmaster91 said:**
> ok, i went to isohunt.com, and got 3 .torrents. i opend them with azureus, but it seems like the download speed is going to slowly. its goin at 30kbs with over 200 seeders. And it says im behind a firewall (unless ubuntu automatically comes with one, im not). and it says i have a NAT problem, wich i have no idea what the means. could somebody tell me if this is average, or is mine screwed up, if so, how do i fix it?

"NAT Problem" is a lay name for an inherent TCP/IP (the protocol collection for the Internet) problem, encountered when traversing routed networks. It's not specific to Linux or Azureus.

The firewall you're behind is very likely some router. You have to setup port forwarding in your router's maintenance web page and set Azureus to use the forwarded port. It should be easy to do, but the flood of specific terminology can cause some headaches. Look at [http://www.azureuswiki.com/index.php/Main_Page](http://www.azureuswiki.com/index.php/Main_Page) for help.

---

### Post by Cardmaster91 on 2006-12-08
ok, i did wat it saidd, i clicked nat/firewall test, and it does

Testing port 54321 ... NAT Error

---

### Post by mahy on 2006-12-08
> **Cardmaster91 said:**
> ok, i did wat it saidd, i clicked nat/firewall test, and it does...


What exactly was the thing you did and what's the make and model of your router?

Also, this is not a Linux-related issue, so you may find more help elsewhere.

---

### Post by Cardmaster91 on 2006-12-08
i went to portforward.com, and folowed their tutorial exactly. the only thing is idk my static ip. i tried using my old one that i had from windows (b/c i didnt think it wuld have changed). but it wont connect with my old one.

and it is kinda linux related, b/c it wiorked fine on windows

---

### Post by mahy on 2006-12-08
type 'ifconfig' to get your IP. i dunno how on earth it can work in windows but not in linux. maybe the problem is somewhere else after all. no idea.

---

### Post by Cardmaster91 on 2006-12-08
ok, i simply had the ip wrong. (and for fture reference, in windows, its as simple as typing "ipconfig",  very similar). But it still says im behind a firewall, it said same thing with frostwire. how can i check if i rerally am behind a firewalll?

---

