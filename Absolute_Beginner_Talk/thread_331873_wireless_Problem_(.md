---
title: "wireless Problem :("
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-05
Hi all ........... Guys when go online  using wireless everythng goes fine 
but when executing 
#iwlist eth1 scanning
   eth1    no scan results 

although i'm online thru wireless 


WHY IS THAT ???????????????????????????????? 




Mba7eth

---

### Post by Frak on 2007-01-05
I'm sorry, but what?, could you restate that in complete sentences? I really don't know what your talking about.

---

### Post by Mba7eth on 2007-01-05
I am online thru my AP(access point) wireless features ..... 
everythings fine as you can see ( posting my msg :D)
but sometimes i want to use another AP located here nearby. I cant see it .
also when typing the command in shell 
#iwlist eth1 scan
    i got this .... 
eth1   no scan results

so i can't even see my AP although i am online thru it .....??? 

So thanks for ur help .... please need to know why ? 


Mba7eth

---

### Post by sailor2001 on 2007-01-05
put in kwifi manager (synaptics)

---

### Post by doobit on 2007-01-05
> **Mba7eth said:**
> Hi all ........... Guys when go online  using wireless everythng goes fine 
but when executing 
#iwlist eth1 scanning
   eth1    no scan results 

although i'm online thru wireless 


WHY IS THAT ???????????????????????????????? 




Mba7eth

It may be because your wireless is wlan0, or ath0, or something other than eth1?
Try running ifconfig and see what shows up as your wirless connection.

---

### Post by Frak on 2007-01-05
> **doobit said:**
> It may be because your wireless is wlan0, or ath0, or something other than eth1?
Try running ifconfig and see what shows up as your wirless connection.
Exactly, the network connection label corrisponds to your chipset, i.e. linsys can be wlan0 and ra0, while there are others like ath0 and Prism cards, for which I do not know the label.

---

