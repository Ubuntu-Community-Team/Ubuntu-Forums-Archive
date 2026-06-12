---
title: "Vmware server and windows client?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by drifting on 2006-06-25
Hi.
New to all this, so here goes.
I have fought with Ubuntu for a few weeks now, and thus far had great fun. However I needed a way to  use Outlook 2003 as that is what we use to get our corporate email. So ever the tight wad, I hunted around, looked at wine(dismissed it) and then came across VMware server, managed to get it all running with help from this forum. I now have a perfect running copy of Vmware, XP and OL2k3 all on my shiney new Ubuntu.

Problem. I cannot for the life of me connect to the Vmware running on my Ubuntu box from my portable. the portable in question runs XP, and the Windows VMware client connects fine to some of our office servers. Now is it something blocking port 902 on Ubuntu? Noticed a setting for SSL conenction on the Vmware server, and thought the MS client may not provide it, that was just a red herring as either on or off it still won't allow me to connect!

I have only installed the server part of the Vmware bundle, wonder if I have missed something here? A telnet to the ip & port show nothing, windows boxes with vmware answer.

Pointers would be great.

Paul.

---

### Post by mips on 2006-06-25
[QUOTE=drifting]Hi.
New to all this, so here goes.
I have fought with Ubuntu for a few weeks now, and thus far had great fun. However I needed a way to  use Outlook 2003 as that is what we use to get our corporate email. [/QUOTE]


Why do you 'have to' use outlook. Will another client not suffice. What do you need in Outlook that cannot be done with something else ?

Just asking.

---

### Post by drifting on 2006-06-25
It's called Outlook over internet and allows a complete cached version of all my outlook data,from our corporate exchange server. Web interfaces just don't cut it I'm afraid.

No problem asking..

Paul.

---

### Post by jwd45244 on 2006-06-25
Try using evelution with the evolution connector for Exchange (All free software)

---

### Post by drifting on 2006-06-26
[QUOTE=jwd45244]Try using evelution with the evolution connector for Exchange (All free software)[/QUOTE]

Sadly Evolution does not support public folders, which is a must for me.

---

### Post by mips on 2006-06-26
The issue is probably something simple, I wish i knew what. Keep at it.

---

### Post by UbieWan on 2006-06-26
Hi

Do you have a firewall installed on Ubuntu? If so that could be your issue. BUT you said you can see other Windows PCs? Also from within VMware install the Windows Client tools, did you do that? Is your portable the same workgroup name? can you go to your corporate webmail site from Firefox? Try and go to the site using IE in XP. You also may need to adjust the firewall in XP running on the box. HTH

Oob

HTH

---

### Post by matrooswolf on 2006-06-26
post 213 from this thread:

[http://ubuntuforums.org/showthread.php?t=183209&page=22](http://ubuntuforums.org/showthread.php?t=183209&page=22)

says port 902 is open by default ...

---

