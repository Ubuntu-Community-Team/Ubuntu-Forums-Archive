---
title: "I keep loosing my internet connection in Gutsy"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by clipse on 2007-10-30
If my laptop is put to sleep for too long I'll try to get on the internet and its a no go. It shows its still connected to my wireless router but I just can do anything over the net. Any ideas? Also, when it does this I'll try to reboot only to have the shutdown "Ubuntu screen" lock up just before it would shutdown. 

What do you guys think?

clipse

---

### Post by blazercist on 2007-10-30
as for the internet locking up is a common problem and unsolved bug.

type 
lspci | grep Net  
in console and post the output.

---

### Post by biomedtech on 2007-10-30
In Feisty, my Internet connection dropped if I canceled a download. Indications would appear as though all were well, but everything timed out.  A reboot was the only way I knew to get back online.  

 When I upgraded to Gutsy, that seemed to be fixed even though Firefox lost the ability to d/l more than one file at a time. Also inoperative is Internet synchronization of the clock. I can set it manually, but I've grown accustomed to millisecond accuracy over the years. I guess the Terminator is having the last laugh now :)

I hope you get a solution soon.

---

### Post by clipse on 2007-10-30
> **blazercist said:**
> as for the internet locking up is a common problem and unsolved bug.

type 
lspci | grep Net  
in console and post the output.

01:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

