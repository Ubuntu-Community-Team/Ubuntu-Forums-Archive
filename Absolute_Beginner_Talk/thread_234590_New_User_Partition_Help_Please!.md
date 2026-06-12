---
title: "New User Partition Help Please!"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Travis_D on 2006-08-11
Hello,

I had a Management Information Systems teacher last semester that basically spent the whole time talking up Linux and GPL. I figured he wasn't just blabbing about something untrue so I ordered some Ubuntu CDs. After booting from the LiveCD, I've become very fond of the OS. I would like to set up my Dell laptop to dual boot from both Ubuntu and Windows. However, I've run in to partitioning problems. I've got a 60GB (down to 51.54) Toshiba hard drive. After reading the guide to partitioning on this site, I am still clueless. First of all, I don't know which drive to select. Secondly, the guide said that by highlighting a drive and pressing enter, a Size option would show up. I'm very confused and am wondering if it has to do with the whole NTFS thing. Please help as I really want to switch to Linux but still don't want to give up Windows just yet.

I've included a screenshot to show you what I'm looking at. For some reason it's missing the rest of the white space in the blue bar and also another darker green box after that. Please advise me which thing to select and the steps I need to take to partition.

Thanks in advance!


-- Travis

---

### Post by xpod on 2006-08-11
you need to use that big unallocated space and "create" a new partition with it then choose that new partition to install ubunto.
Remember to defrag your windows first and you should be ok.

ntfs does seem to have more probs but only when it comes to "writing" to it i believe.

edit:if you`ve already resized then defrag wont matter now

Ps mines on only 3.2g so 9ish gig will be plenty

---

### Post by Greycloak on 2006-08-11
Can you post a screenshot of dirve manager from windows?  If you don't have unallocated space, you may need to use a utility like partition magic to resize your windows partition.  After that you will have an unallocated partition that Ubuntu can deal with.

---

### Post by Drakkor on 2006-08-11
How many hdds do you have and are you trying to install Ubuntu on another drive,or on hda ? IMHO Ubuntu can be installed on what you have left,what about 8 gigs,but with all the extras you may easily go over that, I would get the GParted live CD and look at it from there. I have 2 hdds,and my Ubuntu is dual boot Ubuntu/XP with Ubuntu on hd 2, as shown here:

---

### Post by ovimunt on 2006-08-11
> **xpod said:**
> you need to use that big unallocated space and "create" a new partition with it then choose that new partition to install ubunto.
Remember to defrag your windows first and you should be ok.

ntfs does seem to have more probs but only when it comes to "writing" to it i believe
This is quite inaccurate.

I had a look at the screen shot and I can see a lot of weird partitions on your drive. I would immagine these have something to do with the Dell factory system installation and with the system recovery option that Dell laptops come with.

What you need to do is use some of the freespace on your 54GB NTFS partition to create two additional partitions for linux. One of these needs to be of 2GB minumum but I would recommend 5GB minimum. This will be the main linux partition. You also need to create a small partition, around 1GB, for linux to use as swap space - simmilar to Windows swap space. 

Unfortunately I can't walk you through this step by step because I've never used the Ubuntu utility to do this - I use Partition Magic 8.0 instead.

---

### Post by xpod on 2006-08-11
Whats inaccurate???????That he can use his UNallocated space?????

If you read his post you`ll see that he says his partition is"down to" 51.54g SO i can only assume that BY THAT he means he`s already resized.....no??

And if he`s resized then he would be using the space he`s created ...no??

I am only new to this too but im sure thats about right......by all means please correct me if im wrong

PS  i DO use the ubunto utility....often

---

### Post by djsroknrol on 2006-08-11
is the hda3 being used?..I would combine it with the unalocated space with something like Gparted and then run the installer. Try go go about 1X on a separate swap partition and the rest to the Ubuntu install..

---

### Post by xpod on 2006-08-11
He could still put it on the 8ish gig of unallocated space and just use the fat32 space if he ever needed more space to store stuff.

Thats exactly what i did and do.....I dont have mega gigs to play with so ubunto went on a little slave drive which came up initially as unallocated space and instead of risking playing about with my XP partition/hd i have access to it .

If your only playing around and aint ever going to store mega data then what you have is still plenty.ubunto only takes up a couple of gigs of space to start.and gparted will do it all automatically if you just point it towards the new space....Or you can fiddle about and do it yourself

---

### Post by Travis_D on 2006-08-11
I'll give a couple of these suggestions a try either later tonight or tomorrow morning. I appreciate the help. No computer shops around here will help and I realize it's difficult to troubleshoot over the internet so thanks again and I'll keep trying!

---

