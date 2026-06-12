---
title: "how to increase swap size?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-09-03
i was using 1gb ram , so i set my swap memory to 1.5gb , 
Now i have upgraded my ram to 2gb , how should i increase my swap size?
i am using ubuntu 7.04

---

### Post by jordanmthomas on 2007-09-03
First off, 1.5GB of swap should be more than enough, even though you have more RAM now.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
should provide a good answer.  If you want more swap I'd suggest looking into adding a swap file instead of messing around with your partitions as it's quicker and easier.

---

### Post by meierfra on 2007-09-03
> First off, 1.5GB of swap should be more than enough, even though you have more RAM now.

I agree with  that, unless you have a laptop and use hibernation. In that case (I believe) your swap needs to be as large as your ram.

---

### Post by oilchangeguy on 2007-09-03
> **damansandhu said:**
> i was using 1gb ram , so i set my swap memory to 1.5gb , 
Now i have upgraded my ram to 2gb , how should i increase my swap size?
i am using ubuntu 7.04

you could even do with less swap. go to system, admin., system monitor. and watch how much swap your computer is NOT using. virtual ram is nowhere as fast as physical ram. generally speaking if your computer has to use virtual ram, it's got problems, or not enough physical ram.

---

### Post by insane_alien on 2007-09-03
highest my swap usage has ever been is 432 MB when i accidentally opened every picture on my laptop at once. god that was slow, it was like being on a heavily infected XP machine.

---

### Post by Yizi on 2007-09-03
How can i find out whats my swap is :-s

---

### Post by andyclaxn on 2007-09-03
Hi I did this a few months ago using Gparted, see   

[http://gparted.courceforge.net/generalities/gparted.htm](http://gparted.courceforge.net/generalities/gparted.htm)

   on how to get this program and what to do with it.
The only thing that I needed to work out for myself is that to increase the size of one partition you have to decrease the size of the partition next to it first, so that the unused space thus created is next to the partition that you want to increase. Gparted is a bit slow, but it certainly can do the trick.
Hope this helps

---

### Post by damansandhu on 2007-09-03
ok , then i dont have to increase swap size , thanks for ur help guys.

---

### Post by andyclaxn on 2007-09-03
Sorry,
the link in the above reply doesn't seem to link to the correct page, but it works if you type it in the address bar or cut and paste from here (([http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)))

---

### Post by spacefreak86 on 2008-02-20
Will it damage the current partitions at all?

---

### Post by jordanmthomas on 2008-02-20
Its goal is not too, but there is always the slight chance, so it's best to back up anything you really need.
That said, I have only had gparted mess up twice on me.
Once was on an already messed up ntfs partition and the other was on a dieing hard drive.

I trust gparted though, and when I use it I don't even worry about backing up.

---

