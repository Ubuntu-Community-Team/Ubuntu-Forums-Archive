---
title: "Can't Reach a Command Line"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by rajan on 2007-01-29
Hi all, I have been having a lot of problems after i tried upgrading to dapper. The problem is now at the point where i cannot even get to the login screen where i could hit cntrl+alt+f1 to try and use that terminal. the complete story is below. for right now i am looking for help how i could get to a terminal if i can't get to the log in screen. i tried to figure out how to get to GRUB's safe mode thingy, but i don't think i can get there on my comp. thanks in advance.



FULL STORY:
I tried to upgrade from 5.10 to 6.06 and about halfway through the system went down for a halt. as it started up again, the screen turned on and off a couple of times and then it informed me that the x server couldn't load with my current setup. i looked through the files that it showed me on the screen and both said that there were problems with my keyboard and mouse (they're both pretty old but worked with 5.10). i have no way of changing any of the files on my system because i can't  get to  a terminal. i was going to just reinstall 5.10 with the CD that i have, but i was feeling really smart when i updated and i didn't back up any of my data. an additional question that i have that i can't find an answer to is how can i partition my HD without obliterating any of the old data? can i create a very small partition to reinstall on and still access my old data or will the fact that they're on different partitions block access between partitions? Thanks a lot.

---

### Post by Fasga on 2007-01-29
Try pressing escape while GRUB is loading.

---

### Post by seshomaru samma on 2007-01-29
I think you should reinstall
upgrading is not always succesful
the best way to rescue your data is with a live Cd
If you have access to a CD burner , make yourself a Knoppix CD or even PuppyLinux (puppy is very small so it doesn't take much time to download), or use the Ubuntu live CD .
(Knoppix/puppy are way faster)
Boot from the live CD and either copy your /home directory to a USB flash drive / external harddisk or use Gparted to create a small backup partition to where you copy your data .
Then reinstall.....

---

### Post by rajan on 2007-01-30
thanks Fasga, your suggestion worked. unfortunately, loading grub didn't really do anything (i didn't know it only read from a boot disk... and i didn't have an option to boot into a safe mode or anything) so i have to probably do what seshomaru samma suggested. i'm gonna give those a go (sometime tomorrow). thanks a lot for your help.

---

### Post by rajan on 2007-01-31
Hi Guys,
 I just tried your suggestions and I can't seem to find my old data on my HD. I'm not sure how to get to it because every place i look (where i formerly had data) is completely empty so i don't even have a starting point. although i'm not using knoppix, i'm going to try that shortly, but i have the feeling that i'll be having the same problem (edit--yup, same problem, but i'm going to try the "mount" command). any ideas? thanks.

---

