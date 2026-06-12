---
title: "Netgear WG111T USB adaptor HELP!!!"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-11
I have been going here there and everwhere trying to get info on what I need to do to get the above working on Kubuntu and have drawn a blank.

I read about ndiswrapper etc but also read that this module is included on dapper.

I did lshw and can see the entry for WG111T but flagged as unclaimed...

Can someone point me in the direction what I need to do please.

I have everything wotking on this install for my brother (the convert) but the final thing is his wireless.

Help please......:confused:

---

### Post by Arevos on 2006-09-11
When I installed Ubuntu, I had to install ndiswrapper seperately. Have you done "sudo apt-get install ndiswrapper"? There's also a page on the Wiki for installing wireless through ndiswrapper. The Wiki's currently down for me, though, so I can't provide a link at the moment.

---

### Post by elpuerco on 2006-09-11
Thnx, I think ndiswrapper is already installed.

I ran your command and get the following:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper

If it is the WIKI I am thinking you refer to it sas to use a different method (now out of date) for AMD64 installations!

Totally stumped here :confused:

---

### Post by Arevos on 2006-09-12
I'd try going to the main ndiswrapper site and following the instructions on the wiki to install it from source.

---

