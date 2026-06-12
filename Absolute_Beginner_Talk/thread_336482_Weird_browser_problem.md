---
title: "Weird browser problem"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by 1fastredsc on 2007-01-11
For some reason my browser started hesitating lately. Anytime i go to a site it takes forever, if i continue browsing around different addresses it will be fine. If i let it sit at one address say while i'm reading something, then decide to go somewhere else, it takes forever for firefox to look for the site and connect. At first i thought it was my internet connection but then i tried it on some other computers hooked through the same router going through the same modem and they all behave fine. So is this something wrong with ubuntu and/or my browser?

---

### Post by dbbolton on 2007-01-11
does epiphany 'hesitate' like firefox on that particular computer ?

---

### Post by 1fastredsc on 2007-01-11
I don't know what epiphany is. Gaim does sort of the same thing, takes longer than normal to connect.

---

### Post by MkfIbK7a on 2007-01-11
hey i had the same problem with opera i just switched to epiphany try
sudo apt-get install epiphany
then run it 
hope this helps

---

### Post by 1fastredsc on 2007-01-11
So your saying that it could be firefox? That's wierd since firefox never gave me problems before "with other distros" but i'll look for epiphany and try it out.

---

### Post by Albi on 2007-01-11
Try using different DNS servers.
Find some, edit your /etc/resolv.conf file

Try the servers out

If this solves your problem, search forums on how to make it so the file isn't overwritten on startup.

---

### Post by 1fastredsc on 2007-01-11
I tried epiphany with no change to the problem. 
Where can i find DNS servers?

---

### Post by jamwithbutter on 2007-01-11
Hello, 
If you have tried another browser and have experienced the same problem, it
lets you know that you don't have a problem necesarily with the browser programs
unless there is some kind of flash or java thing going on. And you dont have them 
installed. But I don't think that this is you problem.  
What you would probably want to do when your experiencing the problem is to run
a ping and traceroute when your experiencing the problem. And see what the result is
inorder to troubleshoot your problem.

Ping and traceroute is within the system - admin - network tools.

If your ping or traceroute dies out --- then your haveing a network type problem.
Then you can start troubleshooting for there.

Peace out.

---

### Post by 1fastredsc on 2007-01-11
Ok i think i got it working. Using what albi said with changing the DNS servers, i did some searching and replaced the .conf file and the router settings with the open DNS servers. Now it's actually working faster than it did before, thanks.

---

### Post by SectionThree on 2007-01-11
Here's an even simpler fix to try. Restart the system. I don't know why, but it always works for me (otherwise, I just leave the thing running for days on end).

---

