---
title: "Printing via Netgear PS110 Print Server with HP Deskjet 710c"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by dragonfoundry on 2006-07-29
Im a newbie to linux and I like it (wait for it...)

However, I have a Netgear Print Sever PS110 happily sitting on my home network with a HP Deskjet 710c attached to it. Windows (annoyingly) prints happily while Ubuntu does zippo. 

I have tried the suggestions [Here]("http://www.ubuntuforums.org/showthread.php?t=159717&highlight=ps110") but no joy. 

If anyone has any suggestions apart from giving up all together and using windows to print, fire away.

---

### Post by dragonfoundry on 2006-07-30
Okay for the moment I have given up on the 710c. 

I had a HP 904c Deskjet knocking about so decided to rig that up and pick a fight with it. 

After fighting this is how i got the 940c to work.

1. Ignore the recommended driver select **cdj970**
2. For the connection select **Unix Printer (LPD)**
3. Host - Ip number of the PS110 print server  ( I am assuming you know how to set this / find it out.
4 For Queue put **\p2**

Print a test page and it should work. 

Im going back to the 710c tomorrow for round 34221233 :)

---

