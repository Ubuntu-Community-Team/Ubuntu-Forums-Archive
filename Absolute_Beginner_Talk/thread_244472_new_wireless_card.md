---
title: "new wireless card"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by parushow on 2006-08-26
Hi everybody!

i just bought a wireless card for my desktop
it's a D-Link dwl-g510 (it doesn't have linux driver, but i read somewhere here that this one shouldn't be a problem)

I put the card in the pc and i tried to configure it but unsuccesfully

than i restarted the pc and when ubuntu is loading it stops at 'network devices' or something like that. I removed the wireless card and ubuntu load perfectly

someone knows what I should do ?

thanks guys!

---

### Post by meng on 2006-08-26
So the load freezes completely? It doesn't just stop for 1-2 minutes then report "failed" and then continue? Just checking!

---

### Post by parushow on 2006-08-26
well i didnt get any message
i just waited long (half an hour) and turn it off manually

i was connected with wire so probabily (actually i have no idea) ubuntu was tring to find drivers for the wirless card on internet..

---

### Post by The Mekon on 2006-08-26
I have the same wireless card which is working OK using Dapper.  When I first started using Ubuntu early last year it was necessary to use ndiswrapper however when I updated to Breezy from Warty I got the same problems as you.

The cure was to completely remove ndiswrapper and the card was recognized and was easy to set up under System/Admistration/Networking.

Have you tried Control C when things lock up?  It could be that ndiswrapper is looking for non-existant (and unnecessary drivers).

Brian

---

### Post by parushow on 2006-08-27
thanks brian!

but actually ndiswrapper was not installed

i tried with Control C and it finish loading but freeze again when it should show the first image

---

