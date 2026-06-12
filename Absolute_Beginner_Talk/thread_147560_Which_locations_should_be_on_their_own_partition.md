---
title: "Which locations should be on their own partition?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-03-20
When initially set up Ubuntu I put everything in one partition. I was brand new to Linux and it seemed the logical choice. Now that I have a little more experience I am starting to see the power of having things seperated into different partitions to facilitate upgrades and such.

So far I have moved /home to it's own physical hard drive. Everthing else still resides in the original partition. Which other locations would you all recommend kept separate for convenience? I've seen /opt and /usr mentioned elsewhere. Any thoughts on that or parts to add?

---

### Post by Cirrocco on 2006-03-20
good question

I, as well, would like to hear the answer to this

---

### Post by Princey on 2006-03-20
[QUOTE=pbaehr]When initially set up Ubuntu I put everything in one partition. I was brand new to Linux and it seemed the logical choice. Now that I have a little more experience I am starting to see the power of having things seperated into different partitions to facilitate upgrades and such.

So far I have moved /home to it's own physical hard drive. Everthing else still resides in the original partition. Which other locations would you all recommend kept separate for convenience? I've seen /opt and /usr mentioned elsewhere. Any thoughts on that or parts to add?[/QUOTE]

I may be jumping the gun here, but with the tonnage of reading I've done on the subject matter, 3 partitions should be just fine. While having extra partions can be helpful at times, there's not much benefit to stretching beyond 3. I may be wrong, and subject to correction, but having a partition for /swap, /home, and /root is just about a perfect combination.

---

### Post by Kurt` on 2006-03-20
I normally place /home on a seperate partition, that way users with FTP/shell access can't fill up the entire disk.

Also, one of my friends (who works at a datacenter for a hosting company) says putting /usr on a seperate partition makes it easier to restore a corrupted system from backups.

---

### Post by pbaehr on 2006-03-20
Thanks for the feedback thus far.

I was considering placing /usr on it's own partition so that in the event that I decide/need to wipe the root partition (maybe when Dapper is released) I don't have to reinstall my software in usr/local. Namely, UT2004 which takes FOREVER to load on.

I'll be interested in seeing what some other people suggest as well. I'm guessing it's going to be one of those "whatever suits the way you work best" issues.

P.S. - That's right, "thus."

---

### Post by virgule on 2006-03-20
I have /home, swap and slash (/root if you would). 
Once upon a time I had a /usr partition too but since then I figured out many packages installed stuffs in /bin and what not. So I stick with this threesome and I am happy.

---

