---
title: "Question regarding setting up internet in Ubuntu"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-04-06
Hi!

I am considering installing Ubuntu on my computer, but there is one thing i need to know first..

I have broadband internet at home, but I don't use a router. Therefore I have to connect "dialup-style" (Typing in username and password).
My question is if I can, without to much trouble, do this in Ubuntu, since I don't have the money to buy a router.
In case you're wondering: The reason I don't have a router at this point, is because I got broadband internet 4-5 years ago, when router wasn't included in the ADSL-package of my ISP. Since i've used Windows up to this point, it hasn't been a problem for me to dial up, when the net is just as fast.

One more thing. I decided to completely erase Windows and install Ubuntu, so I downloaded Ubuntu 5.10, burned it to a CD-R and began to install. Formated the windows partition and started the installation. 
When the installation had been running for a while, it froze up in the middle of a sequence. Since this was over a week ago, I don't remember what sequence this was (:-k ), but it was right after the partitioning and formating.

I actually had to install Windows again, try to burn a new copy and start over, but it froze up at the same point, 25% into the sequence. This is not a sequence that takes a while to do, so it looks like it has froze, because I tried to leave the machine for a while, and 4 hours later there was no progress. What can this be? Should I try downloading an older distro, or a new copy of the Ubuntu 5.10 distro? (I have to do this anyway, since I formated my HD completely the second time I tried.)

Sorry if there are any typo's. I am a non English user :cool:

---

### Post by Kapre on 2006-04-06
[QUOTE=wat3r]Hi!

I am considering installing Ubuntu on my computer, but there is one thing i need to know first..

I have broadband internet at home, but I don't use a router. Therefore I have to connect "dialup-style" (Typing in username and password).
My question is if I can, without to much trouble, do this in Ubuntu, since I don't have the money to buy a router.
In case you're wondering: The reason I don't have a router at this point, is because I got broadband internet 4-5 years ago, when router wasn't included in the ADSL-package of my ISP. Since i've used Windows up to this point, it hasn't been a problem for me to dial up, when the net is just as fast.

One more thing. I decided to completely erase Windows and install Ubuntu, so I downloaded Ubuntu 5.10, burned it to a CD-R and began to install. Formated the windows partition and started the installation. 
When the installation had been running for a while, it froze up in the middle of a sequence. Since this was over a week ago, I don't remember what sequence this was (:-k ), but it was right after the partitioning and formating.

I actually had to install Windows again, try to burn a new copy and start over, but it froze up at the same point, 25% into the sequence. This is not a sequence that takes a while to do, so it looks like it has froze, because I tried to leave the machine for a while, and 4 hours later there was no progress. What can this be? Should I try downloading an older distro, or a new copy of the Ubuntu 5.10 distro? (I have to do this anyway, since I formated my HD completely the second time I tried.)

Sorry if there are any typo's. I am a non English user :cool:[/QUOTE]

From what you've written above, you have a dsl connection. You dont need to get a router for this. Just type "sudo pppoeconf" on the terminal and make sure you have your username and password ready as the program will ask this. That's it. If you encounter some error, post again.

K

---

### Post by wat3r on 2006-04-06
Thank you so much. No stopping me now ;)

edit: Anyone got a suggestion what might be the problem with the installation issue.

---

### Post by Kapre on 2006-04-06
water - the error might be due to a bad burn (or bad download). Check the MD5Sum of your downloaded file as this may also is corrupted.

K

---

### Post by wat3r on 2006-04-06
Thanks again!

---

