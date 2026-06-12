---
title: "A couple of things. (Networks and Boots)"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Zibeon on 2007-01-27
Hi,

Well I have been experiencing a few problems,

First: I am running the internet via a DSL G604T router, directly connected through ethernet to two machines. (Friends & My Machine

The strange thing is that on the Ubuntu/Windows machine I can do ping tests, nslookup's in Terminal, but I can't actually use firefox to go to [http://google.com/](http://google.com/), however I can use [http://216.236.39.99/](http://216.236.39.99/) to get to google. So something is wrong with DNS (from what I have read). I did manage to sort this out by using changing the **pcv6** Boolean in firefox, but I can't get upgrades or use synaptic, they try to connect to 1.0.0.0 (which is obviously not going to work) 

So if anyone can help me with that I would appreciate it.

---------------

Problem two is that I can't boot Windows XP.

I have two harddrives, a 200GB SATA for Windows, and a 40GB IDE for Ubuntu.

I have edited the menu.lst and when ever I try to boot windows, it refuses and returns: missing **NTDLR**, I can fix this using fixmbr and fixboot from recovery on the XP CD, but I don't know if that will damage Ubuntu or GRUB (and formatting the Windows hdd is not an option, it's to be left intact).

Or if I repair NTDLR, will I have to use the FAQ "Recovering Ubuntu after Windows install"

I try not to post much and use search but I haven&#8217;t seen anything which helps completely, so I decided to post my exact problem, to try get exact solutions

Thanks for reading and any help you can contribute

---

