---
title: "Azureus shocking d/l speeds!"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by x-to-tha-t on 2007-12-18
Hi all. I'm having some weirdness going on with azureus... I managed to get my download speeds to a sensible figure - around 30-90Kb/s, which was around the average swarm speed. Now just the next day it seems that I have seeds of 26 (66) and peers of 22 (49) d/l at 4.7Kb/s with swarm av. of 54.0Kb/s for my first torrent and the second one at 12 (154) for seeds, 33 (432) for peers, and d/l of 1.9Kb/s with av. swarm speed of 80Kb/s!!! I've heard about people getting steady 100Kb/s downloads and I've done everything I should need to. I'm using an unlimited downloads ISP at 8Mbps connection (actually get about 5.5Mbps). I have forwarded all my ports correctly and installed a couple of plugins which seemed to help when I set them up. I am not using the internet really at the same time, so I don't understand why it has suddenly shot through the floor. A d/l which was going to take 5 hours last night suddenly says it is going to take 5 days!!!

Thanks in advance for anyone who can help me... This is totally frustrating!

---

### Post by aonegodman on 2007-12-18
I downloaded a large game file a couple days ago with the build in torrent downloader in my Firefox with similar seeds and peers you mention and it got up to a steady 585kb/s. But it does fluctuate.

I've used Azurus before under Windows, Could be the extention or plug in Firefox I don't know but it was a torrent file and it downloaded giving the same info and showing me what percent others were using from my connect. It works better than when I used in Windows to me.

Anyway - if you are on DSL wire I know it fluctuates some, but I am on cable. I was told by the cable guy that it is a shared cable system something like Ethernet I guess and demand can effect it. I notice that I can get the best d/l  during late hours, also the server(s) on the other end play the part also. Wish I could be better help.


I'm new to Ubuntu and the Linux scene but I'm like what I'm seeing more and more.

---

### Post by x-to-tha-t on 2007-12-18
So does Firefox come with a built in torrent D/L or is it a plugin, cos that could be useful as my pc is frankly utterly pants and any system resources I can free up are a godsend.

Also it was very late last night - around 11pm to midnight that I was getting these speeds, so it could just be that late on is better.

Thanks for your help!

---

### Post by Lostincyberspace on 2007-12-18
I know I get my best speeds about 1-2am 10-12pm is generally really slow for me.

---

### Post by x-to-tha-t on 2007-12-18
I don't know if this might be something... It seems that my download is capped at 8Kb/s. I've added another torrent to the list and everything has dropped to equal the same total d/l I was getting before... Could this be my ISP capping the torrent D/L rate? I've heard about this happening to people *blatantn00b*

---

### Post by rune0077 on 2007-12-18
> **x-to-tha-t said:**
> I don't know if this might be something... It seems that my download is capped at 8Kb/s. I've added another torrent to the list and everything has dropped to equal the same total d/l I was getting before... Could this be my ISP capping the torrent D/L rate? I've heard about this happening to people *blatantn00b*

Depends on what ports you're using. Many ISP's puts caps on ports 6881 to 6889 (the default BitTorrent ports) in an effort to slow down P2P traffic. You should be able to choose your own ports with Azerus though (not sure, I never really used it), so go check the preferences for something like that.

---

### Post by x-to-tha-t on 2007-12-18
Ah right. No I'm using 49185 (a random number between 40k and 64k). I'll try changing ports anyway, even though it's not that likely. I just find it bizarre that it's not changing at all up or down - just staying at 8Kb/s flat rate.

---

### Post by rickycodie on 2007-12-18
also try and see if azerus will encrypt the data stream for you. that helped me.

---

### Post by rune0077 on 2007-12-18
> **x-to-tha-t said:**
> Ah right. No I'm using 49185 (a random number between 40k and 64k). I'll try changing ports anyway, even though it's not that likely. I just find it bizarre that it's not changing at all up or down - just staying at 8Kb/s flat rate.

That does seem rather odd. Even if an ISP were capping you, I doubt they would slow it all the way down to 8Kb/s. Just at stupid question: are you sure you haven't accidentally capped it yourself in some preference setting (in deluge you can set your own upload and download caps, so it's likely also possible in Azerus, yes?)?

---

### Post by x-to-tha-t on 2007-12-18
I've just checked my config settings... I feel like a bit of a prat... It was me who had limited it to 8Kb/s, but I'm still getting way under the swarm average for each torrent - the averages range from 20 to 90 Kb/s and all I'm getting is 3 to 9. Any ideas? I'll have to keep an eye on it throughout the evening though to see if it gets any better. Thanks for your help - without being asked if I'd capped it by mistake I probably wouldn't even have looked!

Thanks again!

X

Also have now encrypted traffic so will see how that pans out - thank!

---

### Post by Lostincyberspace on 2007-12-18
Let it sit for a while an hour or two and it should pick up.

---

### Post by thelatinist on 2007-12-18
> **x-to-tha-t said:**
> I've just checked my config settings... I feel like a bit of a prat... It was me who had limited it to 8Kb/s, but I'm still getting way under the swarm average for each torrent - the averages range from 20 to 90 Kb/s and all I'm getting is 3 to 9. Any ideas? I'll have to keep an eye on it throughout the evening though to see if it gets any better. Thanks for your help - without being asked if I'd capped it by mistake I probably wouldn't even have looked!

Thanks again!

X

Is NAT enabled?  Have you tried the NAT test?  Do you have a firewall that's blocking incoming connections?

You also might want to try increasing the number of simultaneous connections.

---

### Post by rune0077 on 2007-12-18
> **x-to-tha-t said:**
> I've just checked my config settings... I feel like a bit of a prat... It was me who had limited it to 8Kb/s, but I'm still getting way under the swarm average for each torrent - the averages range from 20 to 90 Kb/s and all I'm getting is 3 to 9. Any ideas? I'll have to keep an eye on it throughout the evening though to see if it gets any better. Thanks for your help - without being asked if I'd capped it by mistake I probably wouldn't even have looked!


:) No problem. As mentioned above, start downloading, and as you get more of the pieces of the file available, the speed should pick up.

---

