---
title: "Where have all the firewalls gone?"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Rastareefer on 2006-06-17
I used firestarter in the the previous version of Ubuntu before I installed Dapper but can not find any firewalls to add under add programs in Dapper. To be honest with you, !'m not even sure if a firewall is neccesary in Linux as I read somewhere that one is not neccesary.
Although, I did the port tests at GRC and failed almost every test.
[http://www.grc.com/]("http://www.grc.com/")

Anyway I did a search for the following programs which turned up no results and am wondering if I am at risk without one in Linux since I am using DSL and don't have a router?



b) Linux
- Firestarter
- Shorewall
- Kmyfirewall
- IPCop
- Guarddog

---

### Post by xael on 2006-06-17
[QUOTE=Rastareefer]I used firestarter in the the previous version of Ubuntu before I installed Dapper but can not find any firewalls to add under add programs in Dapper. To be honest with you, !'m not even sure if a firewall is neccesary in Linux as I read somewhere that one is not neccesary.
Although, I did the port tests at GRC and failed almost every test.
[http://www.grc.com/]("http://www.grc.com/")

Anyway I did a search for the following programs which turned up no results and am wondering if I am at risk without one in Linux since I am using DSL and don't have a router?



b) Linux
- Firestarter
- Shorewall
- Kmyfirewall
- IPCop
- Guarddog[/QUOTE]
I don't think you should worry too much for not having a firewall, since there are currently very few GNU/Linux worms out there, but if having one makes you sleep better at night, Firestarter's just a few clicks away.

---

### Post by Jagot on 2006-06-17
Firestarter is in the universe repo - you will need to enable this to obtain it.  You don't really need a firewall, but I believe it helps in terms of configuration if you need it, otherwise it's a case of messing with config files.

---

### Post by Lord Illidan on 2006-06-17
Better get a firewall to be sure. You never know what can happen.

---

### Post by 5-HT on 2006-06-17
With the exception of IPCop, all of the packages you mentioned *are* in Dapper's repos. 
I am not familiar with IPCop, but from a really quick search it seems to be more of a distribution than a single package.

Most likely, the packages are simply not listed in Add/Remove Applications which only lists a subset of stuff in the repos.

As you upgraded from Breezy to Dapper I'm assuming you know how to enable universe/multiverse and install packages via synaptic/apt/aptitude.

If not, just post back.

Hope that helps.

---

### Post by matjaz_pirnovar on 2006-06-17
Hi,

I would like to install Firestarter too but I'm not sure how to enable universe/multiverse and install packages via synaptic/apt/aptitude.

Could you write brief instructions please? I use Ubuntu 6.06.

PS: I have gone to synaptic under Settings->Repositories but then I'm not sure what to do next. I see listed Ubuntu 6.06 and 5.10. How do I activate "Universe"? And then what follows?


Thanks,

Matjaz

---

### Post by angkor on 2006-06-17
[QUOTE=matjaz_pirnovar]Hi,

I would like to install Firestarter too but I'm not sure how to enable universe/multiverse and install packages via synaptic/apt/aptitude.

Could you write brief instructions please? I use Ubuntu 6.06.

PS: I have gone to synaptic under Settings->Repositories but then I'm not sure what to do next. I see listed Ubuntu 6.06 and 5.10. How do I activate "Universe"? And then what follows?


Thanks,

Matjaz[/QUOTE]

[https://wiki.ubuntu.com/AddingRepositoriesHowto?](https://wiki.ubuntu.com/AddingRepositoriesHowto?)

This explains how you can add repositories.

---

### Post by matjaz_pirnovar on 2006-06-17
Hi,

Thanks. Useful page. Successfuly installed Firestarter.

One question though: Now that I have added Universal category and instalation is done, do I have to remove "universal" again or not?

Thanks.

M  :)

---

### Post by Madpilot on 2006-06-17
[QUOTE=matjaz_pirnovar]Hi,

Thanks. Useful page. Successfuly installed Firestarter.

One question though: Now that I have added Universal category and instalation is done, do I have to remove "universal" again or not?
[/QUOTE]

No - there's lots of other useful & cool stuff in Universe aside from Firestarter.

---

### Post by Rastareefer on 2006-06-18
Phew.....All this to install a firewall.
I am using a fresh install of Dapper and was surprised to not find the firewall in the add programs tool. I am sure it was in the last version of Ubuntu.

I have tried the adding the repositories but am a little confused with which ones to add. I mean, do I add all the "BACKPORTS" both binary and source?

:confused: :confused: :confused:

PS: Out of desperation I just added all of them but even now a program install search still returns nothing for "firestarter".

---

### Post by 5-HT on 2006-06-18
[quote=Rastareefer]Phew.....All this to install a firewall.
I am using a fresh install of Dapper and was surprised to not find the firewall in the add programs tool. I am sure it was in the last version of Ubuntu.

I have tried the adding the repositories but am a little confused with which ones to add. I mean, do I add all the "BACKPORTS" both binary and source?

:confused: :confused: :confused:

PS: Out of desperation I just added all of them but even now a program install search still returns nothing for "firestarter".[/quote] 
You do not need backports enabled. Backports are versions of programs in  the next release of Ubuntu that have ben 'backported' to Dapper.

You only need to add 'universe' to install firestarter (you would have also had to do so on Breezy).
A link to a graphical walkthrough of adding repositories through synaptic was posted a few threads ago.

Did you update your package list after adding the repositories? 

If universe is enabled, the following will install firestarter: ```
 sudo apt-get update && sudo apt-get install firestarter 
``` 
If firestarter is still not found, could you post the contents of /etc/apt/sources.list?

---

### Post by Rastareefer on 2006-06-18
Ah.....It worked after a reboot.

Thanks folks.

---

### Post by 5-HT on 2006-06-18
[quote=Rastareefer]Ah.....It worked after a reboot.

Thanks folks.[/quote] 
Glad you got it working!

---

### Post by jason.b.c on 2006-06-18
Is **IP Cop** really that good.??  I sure hear a awful lot of people talking about it and saying good things..

I wondered if it was all that good..:confused:

---

### Post by ElijahLofgren on 2006-07-09
Edit: Sorry for awaking an old thread, I replied to a post that I thought nobody had answered, but I didn't see that there was another page of posts.

> **Rastareefer said:**
> 
I have tried the adding the repositories but am a little confused with which ones to add. I mean, do I add all the "BACKPORTS" both binary and source?

You should only need the ones listed here: [http://www.elijahlofgren.com/ubuntu/#more-software](http://www.elijahlofgren.com/ubuntu/#more-software)


> **Rastareefer said:**
> 
PS: Out of desperation I just added all of them but even now a program install search still returns nothing for "firestarter".

Make sure you run the following command to update your list of packages after adding the repositories:
```

sudo apt-get update

```

---

### Post by Frank Golden on 2006-07-09
If you're connected to net behind a NAT router and have the 
firewall feature enabled you won't need a software firewall.
If you then run GRC's ShieldsUp you should see passed all Stealth. Network Address Translation (NAT) and Stateful Packet Inspection (SPI) the technologies that enable routers to work also reject unsolicited incoming packages. They do this quietly.
So when you run Steve Gibsons ShieldsUp your router doesn't 
respond, the "definition" of Stealth. You don't get outbound
protection(like when a Trojan or virus tries to "phone home").
Likely not problem with Linux. With linux being open source
and the code of programs suitable for use being available for
scrutiny it is doubtful someone could release a program that could maliciously "phone home". Plus the built in security measures in Linux would prevent a "drive by". I my self use a
Linksys WRT54GL router and don't worry about a firewall.
Have mine in Ubuntu shut off.
I only worry when in XP.

---

