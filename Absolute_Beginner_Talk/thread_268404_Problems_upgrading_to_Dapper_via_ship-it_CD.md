---
title: "Problems upgrading to Dapper via ship-it CD"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Momo88 on 2006-09-30
Hi,

I have Ubuntu 5.10 running on my system and would like to upgrade to 6.06 via an Ubuntu CD that was sent to me via the ship-it service.

I have added the CD to the /etc/apt/sources.list. The 6.06-CD is the only source in there now.

Then I tried sudo aptitude update and sudo aptitude dist-upgrade to no avail. Apparently my system is still checking the 5.10 sources and tells me that there are no new packages available. 

Using the "Actualization Tool" (??? don't know how it's called in English, not Synaptics and in the System folder) I do get the option to upgrade to Dapper via Internet. But I don't want to download 630 MB over a slow internet connection when I have a CD with Dapper sitting on my desk.

Any ideas what the problem could be? Could it be that I can't do an upgrade with a ship-it CD? Is it just to do a new and clean install? I would prefer an upgrade since otherwise I'd probably loose all my settings and being a linux newbie it took me a while to get that far.

Any help and suggestions would be highly appreciated. Thanks in advance!

Yours
Momo88

---

### Post by linear on 2006-09-30
I don't believe you can upgrade via a ShipIt CD - you need the alternate install CD:

> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:[LIST]
[*]creating pre-configured OEM systems;
[*]setting up automated deployments;
[*]**upgrading from older installations without network access**;
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]installs on systems with less than about 192MB of RAM.[/LIST]

---

### Post by Momo88 on 2006-10-03
Thanks for the info!

---

