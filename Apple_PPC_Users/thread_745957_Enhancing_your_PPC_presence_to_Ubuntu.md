---
title: "Enhancing your PPC presence to Ubuntu"
date: 2008-04-05
forum: Apple PPC Users
---

### Post by stream303 on 2008-04-05
Just a reminder that you can let Ubuntu know that your ppc install is alive and well, even if you are just lurking, by voluntarily submitting statistical information about the apps you use, aka a "popularity contest".

You can do this by enabling this in your system preferences.
```
System > Software Sources > Statistics
```

Update: if you want to see the results, just go to:
[http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

Since I'm testing Hardy, I like to submit hardware information as well.  You can find it under
```
Applications > System Tools > Hardware Testing
```

and it will run a series of tests, allowing for your responses, and also your comments on each item tested.  It will submit your hardware responses if you have a Launchpad account.  (popularity contest is open to anyone) That Launchpad account is a good one to have; you can register for one at the top right of the page:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

I just thought I'd point out these two simple ways to reinforce our presence to the Ubuntu devs and others in the community.  I don't know who gets the info, how often it is looked at, or if it is acted upon.  But at least we used the option to do so.

This might help offset the often-touted response of "ppc doesn't get downloaded too much", which doesn't take into consideration that someone can download a single install image and put it on 1000 machines. :)

**I really don't want to start a thread about official / unofficial support**, just wanted to remind everyone of the possibility of providing some simple feedback.  The support thread has been covered waaaay too many times and their position is clear.

Just remind them that we're still here, so we won't find the repo's gone someday soon.

---

### Post by Leopoguin on 2008-04-05
Okay, I added the statistics reporting preference.  I'm more used to commercial software vendors whom I would not be inclined to trust, but I take it Ubuntu will not sell me out.

---

### Post by stream303 on 2008-04-05
They say they anonymize the results, but heck, if an Ubuntu coffee-mug showed up at my door, I wouldn't turn it down. :)

What is more amazing is to look at the actual results.  Looks like PPC is in third place!

[http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

Since the popularity contest isn't turned on by default, I'm amazed at the chart!

---

### Post by ssam on 2008-04-05
also you can vote at [http://brainstorm.ubuntu.com/idea/4296/](http://brainstorm.ubuntu.com/idea/4296/)

---

### Post by Gen2ly on 2008-04-06
wordpress 

:)

---

### Post by stream303 on 2008-04-06
Nice links!  I was very surprised to read that gnome announcement about switching to qt. :)

At any rate, I also found out that since I am using **noatime** in my /etc/fstab I may have been disabling my ability to send back any popularity-contest data with enough meaningful info, so for the time being, noatime has been removed from fstab.

---

### Post by stream303 on 2008-04-13
Update!

I just took a look at Hardy-Beta's  /etc/fstab

and it appears that a default parameter of **relatime** has been added to my root partition in fstab, instead of noatime, which I liked to manually add to fstab in the past.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199427](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199427)

---

### Post by Gen2ly on 2008-04-13
jehosobub, I've read about this before.  Linus gave a pretty good talk getting rid of the atime default.  The new filesystem drivers in the kernel are probably using this new argument.

---

