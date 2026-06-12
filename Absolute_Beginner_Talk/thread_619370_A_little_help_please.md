---
title: "A little help please"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Uberuntu on 2007-11-21
Ok so Ive been tinkering around with Ubuntu (my first taste of linux) for a week now and i am really impressed, so now i want to take it to the next level. As you all know and it pains me to admit, linux doesnt support very many games and the experience is substantially less than playing them on windows. So what i want to do is set up a dual boot  using ubuntu as my primary and then use windows for my gaming needs. I used parted magic to set up the partitions like this: 
1) linux swap 2 gigs
2) ext3 100 gigs
3) ntfs 150 gigs

So i installed windows first with no problem, and then i tried ubuntu using the text installer CD. It worked fine but i couldnt complete the partitioning section of the install because of some problem it had with my how i have my drive partitioned. Ive looked this up in other threads, but all im getting is how to set up a dual boot using 2 hard drives, i am only using 1 split in half. If anyone can help me with some quick n easy advice on how i can accomplish this, it would be Uber-Cool :)

---

### Post by aysiu on 2007-11-21
Is there problem that you don't know how to partition... or that you do know how to partition but it's not working?

> Ive looked this up in other threads, but all im getting is how to set up a dual boot using 2 hard drives, i am only using 1 split in half. This seems to indicate the former.

> i couldnt complete the partitioning section of the install because of some problem it had with my how i have my drive partitioned This seems to indicate the latter.

---

### Post by Inxsible on 2007-11-21
you can have at max of 4 primary partitions in total. You list 3 of them, so you can create 1 additional primary partition (assuming that the above 3 are also primary).

You can also create Extended or Logical partitions. Linux works well even when installed in logical partitions. Windows I think requires it to be a primary partition.

---

### Post by Uberuntu on 2007-11-21
the partitioner works, only it keeps trying to do stuff to the ntfs partition. i want the install to leave it alone compleately, and just install on the ext3. Also i want to be able to choose what OS to boot.

---

### Post by aysiu on 2007-11-21
Have you considered using Windows primarily and then installing Ubuntu as a virtual machine within Windows?
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Uberuntu on 2007-11-21
i was actually thinking of doing it the other way around and have ubuntu as my main.

---

### Post by cotcot on 2007-11-21
Can you tell us which message telling you "some problem" you get in what step of the installation ?

Further you suggest having windows on partition 3 (ntfs) which is not recommended. Windows does not like being on another partition than the first.

---

### Post by Uberuntu on 2007-11-21
for some reason no matter how carefull i am with how i run my computer, windows always ends up suffering from problems.

---

### Post by Uberuntu on 2007-11-21
i wanst suggesting that windows be installed on the ext3. I already have it installed on the ntfs. Anyway when im using the partitioner in text mode i can see all 3 of my partitions and it gives me the options to edit them. i leave the ntfs alone and go into ext3 and change it to be the root and set it to boot. Then i go "done editing these partitions" and it says that there is "an error in the changes ive made". It doesnt say what, but it gives me the option to go back and change them.

---

### Post by aysiu on 2007-11-21
> **Uberuntu said:**
> i was actually thinking of doing it the other way around and have ubuntu as my main.
If it's gaming that's keeping you on Windows, I think it'd be better to have Windows as the host and Ubuntu as the guest. Don't people generally run PC games fullscreen?

---

### Post by Uberuntu on 2007-11-21
either way, cant i install ubuntu on those partitions i made? and just boot into whichever one i need to use. Or does it not work that way for some reason?

---

