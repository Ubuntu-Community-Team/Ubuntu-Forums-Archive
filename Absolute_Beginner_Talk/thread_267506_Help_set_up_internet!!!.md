---
title: "Help set up internet!!!"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-09-28
Please help me set up my internet. I have a 2wire dsl connection. The computer with ubuntu is in another room connected using a ethernet then plugged into dsl filter. Please help!

---

### Post by spyker3292 on 2006-09-28
Please!!!!!!

---

### Post by llamakc on 2006-09-28
I have zero DSL experience, but did you turn the DSL modem thingy off & on?

Are you certain your CAT5 cable is in good shape? 

There are plenty of programs available for setting up DSL. What brand/service do you have? Somebody may have already solved your problem.

---

### Post by spyker3292 on 2006-09-28
> **spyker3292 said:**
> Please help me set up my internet. I have a 2wire dsl connection. The computer with ubuntu is in another room connected using a ethernet then plugged into dsl filter. Please help!

> **llamakc said:**
> I have zero DSL experience, but did you turn the DSL modem thingy off & on?

Are you certain your CAT5 cable is in good shape? 

There are plenty of programs available for setting up DSL. What brand/service do you have? Somebody may have already solved your problem.
I have SBC 2wire dsl

---

### Post by llamakc on 2006-09-28
Have you searched the wiki yet?

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by mongooseman1128 on 2006-09-28
I'm trying to figure out how you've got this all connected. could you tell me stage by stage what and how everything is connected. go with something like: the line from the wall jack to a DSL modem with a built in router and my two computers are connected to the computer 1 and 2 ports (by the way try another port on the back that can help sometimes) and include how the filtering is set up. Also, double check if you can ping (system> administration> network tools> ping and ping [www.google.com](www.google.com)) if you receive responses than your connection is fine try going to firefox typing about:config in the address bar and then ipv6 in the filter and double click the far right column to make sure it says false, then go ahead and try out your connection) By the way, koodos for a good thread title.

---

### Post by spyker3292 on 2006-09-28
> **mongooseman1128 said:**
> I'm trying to figure out how you've got this all connected. could you tell me stage by stage what and how everything is connected. go with something like: the line from the wall jack to a DSL modem with a built in router and my two computers are connected to the computer 1 and 2 ports (by the way try another port on the back that can help sometimes) and include how the filtering is set up. Also, double check if you can ping (system> administration> network tools> ping and ping [www.google.com](www.google.com)) if you receive responses than your connection is fine try going to firefox typing about:config in the address bar and then ipv6 in the filter and double click the far right column to make sure it says false, then go ahead and try out your connection) By the way, koodos for a good thread title.

Computer-ethernet cord-dsl filter-wall

in another room...
wall-DSL box(in another room)-wifi(my computer with ubuntu doesn't have wifi)

---

### Post by mongooseman1128 on 2006-09-28
wait so the ubuntu computer isn't connected the the modem? just to a filter and then the wall jack? If so, that's your problem, you need to have the cat5/6 cable connectwed to the modem and computer

---

### Post by spyker3292 on 2006-09-28
> **mongooseman1128 said:**
> wait so the ubuntu computer isn't connected the the modem? just to a filter and then the wall jack? If so, that's your problem, you need to have the cat5/6 cable connectwed to the modem and computer

so the only way to connect it to the internet is to have a VERY long cable.:neutral:

---

### Post by spyker3292 on 2006-09-28
or work it would if I got a wireless card

---

### Post by mongooseman1128 on 2006-09-28
yeah, what you'd want would either be ubuntu computer to cat5/6 cable to modem or if you get a wireless card (if you get that search for a thread about which brand works best with linux)

---

