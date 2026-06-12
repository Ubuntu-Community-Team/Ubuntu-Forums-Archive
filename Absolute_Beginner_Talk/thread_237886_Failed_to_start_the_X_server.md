---
title: "Failed to start the X server"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by minetto on 2006-08-16
I am a complete newbie to Linux. Sorry if a similar post has been made in the past
if my post seems to be overwhelmingly simple to some or if I'm posting at the wrong place.

The problem I have is that I failed to run the live CD for Ubuntu Linux 6.06 on my system. 
When I am booting on the live CD, I get at some point the following error message:
 
Failed to start the X server... It is likely that it is not set up correctly....
 
My system is:

  os: win xp pro 32 bits sp 2 fr 
  cpu: amd 64 3000+
  mb: asus a8n-e, with phenix award bios v 6.00pg rev 1010
  ram: kington 1 Gb
  IDE HD: 8 Gb free
  graphics: ASUS radeon extreme X700 pci-e

thank you in advance for any help

---

### Post by taurus on 2006-08-16
Do you plan to install Dapper on your machine?  If yes, then perhaps you should consider using the alternate CD since it uses text base, no need to boot into LiveCD first before you can install it.  After it finishes and you still have problem with your graphic card, then you can configure from a prompt with

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by galego on 2006-08-17
if you are still just trying to use the live cd, just boot using safe graphics mode. i have the same card and i had the same problem, for some reason they just dont talk nice at first. once it boots there is no difference in the GUI, is just like the error never happened. if you install however, and you want 3d accel, well that is quite tricky with our cards, in ubuntu at least.
im also trying SUSE enterprise 10 and XGL/Compiz is alive and kicking, same box same card... go figure!;)

---

### Post by minetto on 2006-08-21
sincerely thank you for all those who have sent me an answer, sorry if i have been long to reply.

yes, it worked with safe graphics mode and i havent installed it yet. one of you is talking about another distribution of Linux or UNIX (Suse), which i dont know. how does it compare with ubuntu. 

thanks again and have a good computer time!

:)

---

