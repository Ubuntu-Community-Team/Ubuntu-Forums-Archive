---
title: "&quot;Roll-back&quot; in Ubuntu?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by wat3r on 2007-03-05
Hello!
I'm having some problems after yesterdays fiddling around with Ubuntu, and now I have some ugly problems I would like to get rid off. The stuff I did yesterday was nothing important, so if I loose the work I did then, I don't care ;)
So my question is: Is there any way to "roll-back" or restore the state Ubuntu was in, say the day before yesterday, for example?

---

### Post by hyper_ch on 2007-03-05
If you didn't make backups then the answer is "no" :)

However you can always undo the stuff that messed it up :)

---

### Post by wat3r on 2007-03-05
Hmm. Ok. Because I did some searching around in the forum, and I realized that the problem started when I updated the kernel from 2.6.17-10 to 2.6.17-11. I want to use 2.6.17-10. How do I do that?

---

### Post by hyper_ch on 2007-03-05
during boot, are you presented with the option to load the 17-10 Kernel?

If so, then you can alter the grub config to have the 17-10 kernel booted by default.

---

### Post by wat3r on 2007-03-05
I pressed ESC when I was told that I could, and "voilà". I got to load 17-10 kernel :) I will be hanging on to this until there is a fix for wireless network in 17-11.

---

### Post by floke on 2007-03-05
You can also use partimage to create an ISO of your partition should you want to restore it to a previous state later.

---

### Post by wat3r on 2007-03-05
> **Steve.K said:**
> You can also use partimage to create an ISO of your partition should you want to restore it to a previous state later.

Ok. I found out it was better to load the previous kernel, since none of my settings were lost.

---

### Post by drs305 on 2007-03-05
> **Steve.K said:**
> You can also use partimage to create an ISO of your partition should you want to restore it to a previous state later.

Steve.K

I am a linux newbie. If I create a partition on a new computer and then save an image using partimage to this partition, would I be able to copy it to the active partition for a full restoration of the computer existing at the time I made the image? Or would certain files be in use and therefore not subject to copying or restoration? 

Hope the question makes some sense. Thanks.

---

### Post by floke on 2007-03-05
The bottom line is that I've never actually tried to restore a partition in this way, although I've saved a copule of images just in case. I think that what you say is feasibl - i.e. you save an image of partition a to partition b, and then restore it from b into a. Since you have to run partimage of a liveCD, none of the actual files on the HDD are in use.

For more on this I suggest you read [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Hope this helps

---

