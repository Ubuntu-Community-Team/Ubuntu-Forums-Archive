---
title: "Slow torrent speeds"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Shai Hulud on 2007-02-17
Hello, Linux newbie here.
I have troubles with torrents download. After about one day of testing with different programs, reading trough the forum, cursing, reading again, cursing again, i've decided it's time to ask for help. So the outline:

Ubuntu 6.10
Torrent programs tested:
Bit torrent, Azureus, KTorrent, uTorrent /with wine/
I have no router or stuff - real ip connected directly to the internet. The torrents i try to download, are well seeded /actually under Windows i hit about 700-800k, so i it's not bad seeding issue/.
Azureus is saying that everything with my connections is OK, uTorrent also. So i'm not firewalled or inaccessible. Also, it's not upload crippling case, because under Windows i set my Max Upload Speed to 50, and there are no probs. Under Ubuntu i've tried with 5 kb - still no luck. I've disabled IPv6, because i've found threads here, suggesting that it may be the problem.

I'm getting despaired here, can someone give me hints at what i'm doing wrong :confused:

---

### Post by buuntuu! on 2007-02-17
are your ports open?
follow this  [howto]("http://ubuntuforums.org/showthread.php?t=331161")

---

### Post by Shai Hulud on 2007-02-17
Hm, i see this for the first time, it hasn't popped in the previous searches.
But it didn't fix the problem :(
My download speed is still 10k or so...

---

### Post by kinematic on 2007-02-17
try using a port in the 50000 range.
many isp's throttle the lower ports.

---

### Post by Shai Hulud on 2007-02-18
As i've said, under Windows everything is OK, so my guess is it's not my provider... I'm under Win now, and the same torrents were downloaded instantaneously with speeds way over 400-500, while under Linux the speed was about 10-15. And the seeders are about the same number /actually they are about 50 less, than yesterday/, so bad seeding wasn't the problem as i've posted earlier.

I've found many threads with the same issues described, and it seems that everyone suggests the exact same things, which as in my case are specified already, that are not the problem creator.

Everyone is like 'Check your ISP' Hey! Under Windows things are normal, or what there is ISP conspiracy that detects you using Linux and screwing your torrent speeds.

Or 'You, know, torrent technology is complicated, and there have to be seeders'. Why is the lecturing tone? In many of the posts, people are saying that under VMWAREd Windows machine in the Linux box things are ok, but not in Linux, so the bad seeder issues are not the problem.

I'm starting to think, that nobody reads the whole posts, only see 'Slow torrents', thinks 'Just another lame wanna-be-pirate or stuff' and posts the lecturing about seeders and ISP stuff.

Sorry for bashing, but i'm very frustrated. This thing is very spread issue, but in the forum there is NO solution. :confused:

---

### Post by erealz on 2007-02-20
i to have the same problem exactly and no one has an answer as to why this is?!

---

### Post by xadloki on 2007-02-20
Same exact problem over here, I've disabled IPv6 Globally and in Firefox, I've opened ports, I've reset my router and triple checked EVERYTHING... still no effect and no one is helping me out in IRC always repeating the same over and over... I even have all green smilies in Azureus and really healthy torrents and my speed ? 25 KB/s up and 3 KB/s down (and yes 25 is the limit I set it to so it's not slowing down my DL)

---

### Post by gloscherrybomb on 2007-02-20
same problem. all lights are green.

---

### Post by Kuoi on 2007-02-21
My experience with Torrents is that the only 'fast' client is "Wine + Utorrent" .

I was downloading 2 files , and with Ktorrent it would take days ...
I've decided to install Wine + Utorrent , and downloaded the same Torrents to the same folders , and guess ..;
Utorrent was checking the Ktorrent parts , and resumed them , and it is MUCH faster !
Now it will only take hours , NOT days .

It seems there's nothing like Utorrent.

Kuoi

---

### Post by gloscherrybomb on 2007-02-21
Thats all very well but it doesn't address the issue of why azureus isn't working properly in ubuntu.

---

### Post by HereInOz on 2007-02-21
Just checking, because nobody has actually stated this, that the ports you are opening are on the IPtables firewall which is activated in Ubuntu?

You probably are, but I thought it worth a mention because some people are not comfortable with IPtables, and some don't even know it is there.

If any of you are wanting to open ports in the Ubuntu firewall (IPtables) then you can use Firestarter which is a gui type of thing, and makes configuring your firewall much easier.

Other than that, I will shut up, for I have no other ideas to offer.

---

### Post by gloscherrybomb on 2007-02-21
Surely as all the lights are green (including NAT) then the firewall isn't a problem?

If the light can still be green even though the firewall is on then maybe that's the problem.

---

### Post by xadloki on 2007-02-21
Firestarter is what I used to open up the necessary ports and looking from the network activity azureus is making the connections through the specified port. Also set the router to be DMZ for this PC and still didn't work... I'm going to try out uTorrent now and see if it works better.

---

### Post by userundefine on 2007-02-21
What torrents are you testing on?  I'm not going to say that "torrent is a complicated technology" but the swarm does ALWAYS dictate the speed if you have no other impediments.  It's highly possible that you're 1) connected to poor swarms, 2) getting crap data from crap torrents, 3) getting snubbed, 4) several other possibilities...

Nearly any torrent client (save BitComet and other cheaters), properly configured, will render the same speeds.  This is not a linux issue.

I suggest you test an openoffice torrent since they're always very well seeded and very fast.  I consider it the barometer for properly configured BT clients.  [Try it.]("http://linuxtracker.org/download.php?id=3286&name=OOo_2.1.0_Win32Intel_install_en-US.exe.torrent")

---

### Post by xadloki on 2007-02-21
Just installed Wine and uTorrent and pretty much maxed out my connection full speed :)

---

### Post by grogger13 on 2007-02-21
What do you mean Bitcomet and other cheaters,  When i use windows i always use bitcomet and i love it.

---

### Post by xadloki on 2007-02-21
For what I hear Bitcomet takes advantage of super seeding or some sort in an unfair way... That's why recently it's getting banned.

---

### Post by gloscherrybomb on 2007-02-22
I have the same issue with the Open Office torrents.

I'm sure if I used utorrent and wine I would get full speeds as well, so clearly it's an Azureus-linux compatibility issue. Any ideas?

---

### Post by hoagie on 2007-02-22
Did you enabled enscryption. Go to Options>Transport Enscryption> Enable.
It boosted my speed pretty much.

---

### Post by xadloki on 2007-02-22
While I did try to add encryption in Azureus my speed went up from 5  to 30 KB/s but that was the the highest it reached and I kept it on for 1 hour to see if it would go faster. With the same torrent in uTorrent the speed wen't up to my max (100KB/s) in less than a minute and steady from there on. And I have used Azureus for over a year in Windows so I'm very familiar with how to set it up to get the best speeds. I also tried Deluge but wasn't able to get it working. Deluge would have been the best choice I think but it is a pitty that it did not work.

---

### Post by paculz on 2007-02-22
> **gloscherrybomb said:**
> Thats all very well but it doesn't address the issue of why azureus isn't working properly in ubuntu.


Try using bit commet or Azureus for linux rather using it through Wine.

---

### Post by gloscherrybomb on 2007-02-22
^ Same with me.

---

### Post by userundefine on 2007-02-22
> **grogger13 said:**
> What do you mean Bitcomet and other cheaters,  When i use windows i always use bitcomet and i love it.
[http://www.google.com/search?q=bitcomet%20cheating](http://www.google.com/search?q=bitcomet%20cheating)

---

### Post by gloscherrybomb on 2007-02-22
> **paculz said:**
> Try using bit commet or Azureus for linux rather using it through Wine.

I am using azureus for linux.

---

### Post by gloscherrybomb on 2007-02-22
PROBLEM SOLVED:

OK, some people may have the issue described above. Azureus may be configured properly with your router, i.e. port forwarding or UPnP, and this results in all the lights on Azureus being green. Therefore you can't determine what the problem is.

The problem is, that the default ubuntu firewall is blocking azureus and azureus doesnt let you know about it.

How I solved it:

Download firestarter from repos.

STOP the firewall. (make sure it is unlocked).

Check azureus to check the performance has improved.

If so, then this is definitely the problem. Now you can add the correct rules, and turn the firewall back on. If you've done this correctly azureus should maintain its performance.

Sorted!

---

### Post by anv on 2007-02-24
when using firestarter how can I describe tcp or udp for that, if I take the rule for bittorrent 6881-6889 I think they are just tcp ports and to share it would need udp?!?

I used azureus with this same machine under fedora 4-6 - perfect , then I installed it under Dapper - I had some problems but I could download when it gave dht firewalled, but now on this edgy It is impossible to get it work, it slows  down after couple of minutes and finally all torrents stop quite soon, even I would have, ports open from my router, and firestarter( Itried to turn off firestarter and it helped some minutes it was fully green then it tells stopping first downloads dht firewalled)

---

### Post by nonewmsgs on 2007-02-24
can we sticky this please

---

### Post by gloscherrybomb on 2007-02-24
I think UDP is already enabled. Anyway you shouldn't be using the default port in azureus, try something like 55555. the default port is often blocked and you'll get low speeds.

---

### Post by xadloki on 2007-03-02
Okay... for the past week I've been trying diferent ways and testing with different routers and while I've gotten both Deluge an Azureuses speeds up to my max with healthy torrents there is something diferent about uTorrent (+Wine). Poorly seedes torrents in uTorrent max out my connection speed (110KB/s) while the same torrent only reaches 15-35 KB/s in azureus or deluge. So pretty much I'm going to stick with uTorrent because it really is alot superior to other clients IMO.

---

