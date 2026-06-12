---
title: "packet sniffing"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-03
i decided to take a look at whats in these packets im being sent.

i downloaded ethereal from the repositorys.
i sniffed for about 15 mins.a couple of packets that were sent to port 1026/27 were showing data for a pop up. go to this site and download this etc.telling me my windows registry is critical.
i know this packet was aimed at the messanger service.

the thing i want to know is about the udp packets.one of them had ping written in the data area.i was wondering if this was a ping echo request as i always thought ping requestes were icmp.
anyway, do i have to decode these packets in some way? iv been googling but i not sure what it is i should be looking for.
i basicaly want to understand what these packets mean and i can only see them as a load of numbers.
ethereal has an option to decode them if you choose a format.the list is huge and i need to figure out how to know what to choose.

i know this isnt strictly speaking a ubuntu question but you guys seem to answer most questions and the other forums iv visited aint reply'd all night.
well i suppose it is actually seeings as though you might have to recomend a ubuntu software package.

---

### Post by uk_sphinx on 2006-10-03
you guys do realise im sniffing incoming traffic to my home comp right??
i aint doing nothing illegal

---

### Post by skymt on 2006-10-03
Why do you care? Messenger noise is common. As are worms and random port scans. Security researcher Steve Gibson calls it "IBR" or Internet Background Radiation, meaning "just ignore it, it doesn't mean anything". Just get behind a [router](http://netgear.com/).

---

