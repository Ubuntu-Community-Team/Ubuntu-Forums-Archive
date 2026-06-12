---
title: "Server Rebuild"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Mikey_MW on 2006-06-10
I have a friend who is constantly inundating me with old PC parts (because they work at a PC repair store) and I have recently got a server motherboard (takes 2x 1.4Ghz Celeron) that I plan to turn into a file server.

Does Ubuntu support multiple processors? If so, what ISO do I need to download. Also - does Ubuntu have any known networking issues I should know about? I know that it will be connecting to the internet (sharing the connection across three PCs) and will be connecting to 1 Ubuntu PC, 1 Damn Small Linux PC, and 1 BeatrIX PC. 

Does anyone think I should be using perhaps another distro for this server?

Thanks.

---

### Post by blackjack6.21.91 on 2006-06-10
I've read that Ubuntu does support multiple processors.  I've also read that you will recieve a major speed boost if you download the correct kernel for said processors after burning your ISO.

Ubuntu can be used as a server (although I don't know if it's the best server OS, I've actually heard good things about freeBSD).  

I think you would download whatever ISO your box supports.  No different than single processor.  Just remember to download the server ISO..

I think networking is pretty smooth between UNIX boxes.

---

### Post by Mikey_MW on 2006-06-10
Ok, thanks for that, it makes a lot more sense now. I think I will have a look into that other OS, just so I can find the perfect one for me... 

(as you can probably tell with the 3 PCs, I'm trying out different distros right now)

---

### Post by tronica on 2006-06-10
ubuntu as a server makes a great server OS, just download the normal X86 version and install the smp kernel and that will let you use two procs or  procs with HT.

---

