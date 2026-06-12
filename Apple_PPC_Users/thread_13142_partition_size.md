---
title: "partition size"
date: 2005-01-29
forum: Apple PPC Users
---

### Post by ewaldgroup on 2005-01-29
Im getting ready to repartition my ibook 30gig so i can install ubuntu on it. I have Mac OS 10.3.7 right now and OS 9. how much space should i give to Ubuntu? I was thinking about 6gb. It wouldnt be my main system, just to mess with for now. Would I partition it as "free space" or hfs+?

Thanks,
ewaldgroup

---

### Post by DJ_Max on 2005-01-29
6GB would be fine, but I'm pretty sure you'll like Ubuntu, so might wanna give it a little more like 12GB, and for partition format use "free space".

---

### Post by Viro on 2005-01-29
[QUOTE=DJ_Max]6GB would be fine, but I'm pretty sure you'll like Ubuntu, so might wanna give it a little more like 12GB, and for partition format use "free space".[/QUOTE]
 I'd say 10GB. Reason? My current install takes about 4 GB. And I have a 2 GB swap partition. You'll want to have some space for your own data as well.

---

### Post by ewaldgroup on 2005-01-29
Ok. Thanks for your input. I am going with 8gb. I can't give it 10-12 right now because i need the space for os x, but mabby in the future. How inportant is a 2gb swap? what does the swap partition do?

Thanks,
ewaldgroup

---

### Post by DJ_Max on 2005-01-29
Normally the swap is set to 2 times your ram. I have 256mb of ram, so my swap is 500mb. I think it's some type of unwritten rule. :o

Swap is used sorta like ram, as Linux handles memory differently, Linux always allocates memory to a process from the free memory pool, and doesn't releases memory from completed processes until it needs to. So, no matter how much memory you have, it will end up being totally used - sooner or later. Thats where the swap comes in.

---

### Post by Viro on 2005-01-29
Swap provides you with virtual memory. On Windows and OS X, virtual memory resides on the system partition, while in Linux, you assign a whole partition for swap. It's meant to be slightly faster, i think.

Yeah, a good rule is 2x memory, but if you know how much RAM you applications will take, you can always break the rule. After all, rules are made to be broken ;).

---

### Post by ewaldgroup on 2005-01-29
Once again, thank you for all your help. That goes to everyone. the 2x ram rule is cool. Thanks.

Thanks,
ewaldgroup

---

