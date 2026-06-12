---
title: "Waking from Suspend -&gt; No Wifi Adapter"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-05
I am sure I came across one or two threads about this, but I can't find them and I am not sure if there is an 'official' solution to this problem.

OS: Dapper
Asus A6K Laptop

As the title say, when I wake my laptop from suspend mode, then Network Manager informs me that my wireless adapter could not be found, it seems Dapper is not waking the wireless adapter card.

Can anyone tell me how I get Dapper to wake the wireless adapter card after suspend mode?

TIA.

---

### Post by PartisanEntity on 2006-12-06
Just a polite 'bump'. Has anyone else experienced this on their laptop?

---

### Post by gn2 on 2006-12-06
I had similar issues for a time, but cured it by just removing and replacing the (cardbus) adapter.

Tricky if it's the "built-in" type though.....

---

### Post by PartisanEntity on 2006-12-06
Any non-invasive methods? :)

---

### Post by PartisanEntity on 2006-12-07
Surely others have experienced something like this?..(bump)

---

### Post by zigot on 2006-12-09
I have the same problem on my ThinkPad T23. I'm still looking for the solution.

---

### Post by PWill on 2006-12-09
When you wake from suspend/hibernate, right-click on NetworkManager, and uncheck `Enable Networking'
Then right-click again, and check `Enable Networking'
For me, this causes NetworkManager to rescan for networking devices, and I can then connect again.

---

### Post by PartisanEntity on 2006-12-09
hmm interesting, ill try it out and post back, thanks.

---

### Post by PartisanEntity on 2006-12-09
> **xiamcitizen said:**
> When you wake from suspend/hibernate, right-click on NetworkManager, and uncheck `Enable Networking'
Then right-click again, and check `Enable Networking'
For me, this causes NetworkManager to rescan for networking devices, and I can then connect again.

Thanks for the suggestion, it worked :)

---

