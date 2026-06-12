---
title: "Torrents in Edgy Eft - help.."
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-09
Heyall

I installed Edgy for the first time a few days ago after running Dapper, and it seems to be running smoothly. I like it too. But when I try do download using a *.torrent file, I run into problems. Azeurus won't even open unless I "sudo" it in term. And when it does open, it downloads at 1 kb/s or less. BitTornado connects and all, but downloads at 2 kb/s only. I tried changing settings but nothing works. Is this a known bug in Edgy, that *.torrents don't work? Trying to install kTorrent now, to see how it fares. 

Anyone with ideas? I have no router, pc is connected directly to the modem, and no firewall present.

---

### Post by Sef on 2007-01-10
> Azeurus won't even open unless I "sudo" it in term. And when it does open, it downloads at 1 kb/s or less. BitTornado connects and all, but downloads at 2 kb/s only. I tried changing settings but nothing works. Is this a known bug in Edgy, that *.torrents don't work?

I use Bittorrent, the Gnome default, and works fine.   Have you ininstalled the others first before downloading the new torrent loaders?

---

### Post by blackened on 2007-01-12
You're download speeds sound like a NAT problem. Try checking your port settings in whichever program you are using against your router/firewall/whatever and change them if need be.

Where do you have Azureus installed to?  You may need to change its permissions with a handy dandy sudo chmod 755 on the Azureus startup script.

---

### Post by Kateikyoushi on 2007-01-12
Did you try it with more than one torrent ?
I can go full speed on my connection using rtorrent.

---

### Post by gardara on 2007-01-12
try rTorrent :)

---

### Post by Pobega on 2007-01-12
I used to use Azureus and I got pretty sluggy speeds behind my (opened) firewall. Now I use btdownloadcurses, I unblocked TCP 6881-6889 and everything downloads fairly quickly. I advise you at least try it.

---

### Post by gardara on 2007-01-12
6881-6889 are official torrent ports and blocked by many private trackers, I advise you to use other ports than them.

---

### Post by blackened on 2007-01-12
> **gardara said:**
> 6881-6889 are official torrent ports and blocked by many private trackers, I advise you to use other ports than them.

That port range is also blocked by some individual ISPs. I run Azureus on port 55000 and it works fine.

---

### Post by QuicksilverKev on 2007-01-12
I agree... its normally port forwarding that causes it.

I use Ktorrent, and often pull big speeds down (over 200k is normal), but I am on a 10mb line.

---

### Post by stimpack on 2007-01-12
I also have torrent problems since installing edgy. I have been booting into Windows to download which is very annoying. Ports/Firewall all fine.

---

### Post by hyper_ch on 2007-01-12
Well, I haven't had any problems with KTorrent on Xubuntu

---

### Post by blackened on 2007-01-12
> **stimpack said:**
> I also have torrent problems since installing edgy. I have been booting into Windows to download which is very annoying. Ports/Firewall all fine.

If you're using Azureus, then sometimes the port configuration dialog can be flaky. I don't know how many times, during setup, I changed my port settings only to go back 10 minutes later and find that they had reverted to the defaults. Minor annoyances make life more fun. Or at least so I try to convince myself.

---

### Post by erv2 on 2007-01-17
> **sjau said:**
> Well, I haven't had any problems with KTorrent on Xubuntu

hi, i am using KTorrent on Xubuntu as well, the speed looks alright, but it's eating my hardware resource up. my machine is a Compaq Armada M300 laptop, which only has 192MB ram and 600Mhz Pentium CPU.

everytime i start KTorrent, i notice there's a lot of swapping between memory and harddisk, and i cant do anything else like firefox.

is it a known problem that using KDE stuff on XFCE will slow the machine down a great deal?

thanks.

---

### Post by hyper_ch on 2007-01-17
I think KDE Appz will slow down Xfce... however I did not choose Xubuntu because I can't properly run KDE, I chose it becaue I like it better :) I don't need all that extra stuff...

---

