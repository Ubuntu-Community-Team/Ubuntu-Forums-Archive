---
title: "vlan/multiple networks"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by tekwarren on 2006-02-10
When I first started using Ubuntu it was kind of a pain as the building I start my day at is not yet part of the vlan at the main office where I work from in the afternoons. I had no issues using dhcp at the first building but I had to manually set my IP etc at the other. My supervisor (network manager) has also been using linux more and to make things simple for us he set our vlan to use dhcp...but our same static IP's are assigned via mac address. All that works perfectly and I can now leave dhcp settings with no hassle of changing. Well every morning now it seems I have to disable/enable the eth0 device in order for it to see the network. I can connect to the wlan right off the bat if i want to but i'd rather use ethernet. I shut down before heading to the other office and I don't have any problem with dhcp being optained right away over there. I don't know why one one network requires the eth0 reset every day...the wiring here is crappy and old (hopefully being replaced soon) and another thought is maybe that the port on the switch is "dumbed down" to 10mb (another result/temp fix for crapy old wire). Any ideas as to what could be the issue?

---

### Post by tekwarren on 2006-02-13
no ideas or suggestions? I continue to have to de-activate / re-activate eth0 at this building but am able to pick up dhcp at my other office and at home with no problem at all.

---

