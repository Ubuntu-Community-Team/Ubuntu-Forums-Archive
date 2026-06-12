---
title: "ubuntu wont install"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by insub2 on 2005-12-09
i checke the md5sum. it's right.  i burn the iso image to a cd and put it in my comp.  it starts the install process and everythings fine untill the base system is installing.  when it gets to the kernel, it stops and has an error.  if i re-partition, it will stop again the same way.  if i don't partition it and run the install base system again, it asks me to choose between linux-386, linux-image-386, and linux-image-2.6.12-9-386.  i picked linux image-386 umm becuase. 

when installing the remaining packages, it always errors.  
it'll let me "finish installation" and when it restarts my comp, i get a black screen with white type that aks for my user name and log in.   after that, it says "apathy@apathy:~$"

what should i do???

---

### Post by linbetwin on 2005-12-09
There might be several causes:

1. Did you choose to do an expert install?
2. Did you create the partitions or did you let the installer do that? Make sure that the root partition (**/**) is flagged as bootable (**on**).
3. What size is the partition that you want to install Ubuntu on? It should be at least 3 GB.

---

### Post by jorn on 2005-12-09
Can you post the errors you get?
By the way:"apathy@apathy:~$" is a command line program like dos in windows. 
Jorn

---

### Post by Gray. on 2005-12-09
apathy@apathy:~$ means that you are logged onto computer "apathy" with the user "apathy".
Try typing ```
startx
``` and tell us what happens.

---

### Post by Gray. on 2005-12-09
Oops. Sorry.

---

### Post by insub2 on 2005-12-09
[QUOTE=linbetwin]There might be several causes:

1. Did you choose to do an expert install?
2. Did you create the partitions or did you let the installer do that? Make sure that the root partition (**/**) is flagged as bootable (**on**).
3. What size is the partition that you want to install Ubuntu on? It should be at least 3 GB.[/QUOTE]


1. i dind't choose anything
2. i let the installer do the partition
3. it was about 10 gb



also i figured out the command line thing by looking around the forum and ubuntu site.

---

### Post by insub2 on 2005-12-09
i figured out what the problem probably was (certainly A problem) and i feel like a dumby.

i was trying to istall ubuntu on an old computer and i didn't check the memory untill just now.  a whopping 64M -96M with the RAM stick from my roommates busted eMachine.  looks like i either need to buy some RAM or ...
is there a distro that requires less memory?

---

### Post by DeathKnoT on 2005-12-09
[QUOTE=insub2]i figured out what the problem probably was (certainly A problem) and i feel like a dumby.

i was trying to istall ubuntu on an old computer and i didn't check the memory untill just now.  a whopping 64M -96M with the RAM stick from my roommates busted eMachine.  looks like i either need to buy some RAM or ...
is there a distro that requires less memory?[/QUOTE]
yeah , these are ones that people here recomended for me they should work for you.
**[FeatherLinux](http://featherlinux.berlios.de/)**  and
**[DamnSmallLinux](http://damnsmalllinux.org)**

---

