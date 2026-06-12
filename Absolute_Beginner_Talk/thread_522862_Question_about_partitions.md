---
title: "Question about partitions"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by caramelsoul on 2007-08-11
OK, so i have had Ubuntu 7.04 installed for two weeks now and am very happy with it. When installing instead of manually setting up partitions i just pointed it to an unused hard drive and allowed it to format it and use that for the sole use of ubuntu. (Note, this was a dual boot. Primary HD is windows and primary slave is ubuntu). 

But now i have been reading the forums more should i have made separate partions for swap and dev? If so can i still do that now without having to reinstall?

I now have most of the programs i need for music, video, usenet with unrar and par2. I also feel very comfortable using ubuntu (and surprisingly so does my good lady) so feel i can now get rid of windows entirely. I have 4 hard drives, 3 x 250GB and one 120GB which is the ubuntu one. So should i move the media about and format each drive to Ext3 or keep NTFS?

Thanks for reading and i look forward to replies...

---

### Post by MenZa on 2007-08-11
Ubuntu should have created at least a seperate swap partition. Could you paste the output of the following:

```
cat /etc/mtab
```

---

### Post by caramelsoul on 2007-08-11
I would but im not at my home PC at the moment. I wont be for another two weeks either as i am at work (offshore). Im just trying to decide what i should do next, you know, i get bored at work sometimes. ;)

---

### Post by armandh on 2007-08-11
a good live partitioning program is handy to both observe and to change
I am partial to [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by antoz on 2007-08-11
You could split the Ubuntu partition and create a separate "home" a bit like my Documents in windows, that way if you ever need to reinstall you keep all your files and settings. you can use the live Cd to do that as it has Gparted on it.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by caramelsoul on 2007-08-11
Thanks very much for the replies guys. I may try and mess about with this on my Laptop that i have out here at work first before i go home and make a real mess of things...;)

---

