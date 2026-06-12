---
title: "I reinstalled and now I have two partitions."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-15
I seem to have a special genius for messing up the simple. I got into some trouble and I reinstalled 7.10. Now instead of one  I seem to have two separate iterations of Ubuntu. How do I get rid of the one I don't want?

---

### Post by taurus on 2007-12-15
Use gparted in System -> Administration (install it if you don't have it on your machine with synaptic) and remove/format the partition that you don't want.  Mount it somewhere and use it as a storage.

But if you want to merge that space to your current partition, then you have to do that from the LiveCD.

---

### Post by boriquajake on 2007-12-16
> **taurus said:**
> Use gparted in System -> Administration (install it if you don't have it on your machine with synaptic) and remove/format the partition that you don't want.  Mount it somewhere and use it as a storage.

But if you want to merge that space to your current partition, then you have to do that from the LiveCD.

I installed gparted but I am too afraid to use it to delete anything. Also, I have no idea what it means to "mount" a partition, but thank you for the tip, though,  I can tell that as I get a little more experienced that program will be very useful.


Could anyone point me towards a "how to" guide for gparted?

---

### Post by rexxxlo on 2007-12-16
this guy has helped me a lot ,here is his website

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by boriquajake on 2007-12-16
> **rexxxlo said:**
> this guy has helped me a lot ,here is his website

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Thank you so much. That site has exactly the info I needed.

---

### Post by boriquajake on 2007-12-17
> **boriquajake said:**
> Thank you so much. That site has exactly the info I needed.

OK, now I feel like a dork. I got all excited about the information on that site that I didn't really look for the specific issue I needed to deal with.

I downloaded and installed gparted. I start it up and it shows me the different partitions on my HDD but I do not really understand what it is telling me about them. I am afraid to just guess. Could someone take a look at the screenshot and tell me what needs to be deleted or changed or whatever?

Thanks in advance.

---

### Post by viking777 on 2007-12-17
I'm going to tell you what I think, but beware, I have been known to be wrong! So before you rush into deleting things perhaps get a second opinion OK?

One thing I can be certain of is that you dont need 2 swap files as you have at the moment(sda5,sda7). So you can certainly delete one of those (personally I would have 1 swap file of about 512Kb unless you are heavily into video editing or some such similar activity).

The next thing I cannot be so certain of but I think your rogue partition  is sda3 because it is mounted as /media/disk which basically means that it is being seen as some kind of external media like a large usb key for example. Easy to tell though, open a file manager like konqueror, dolphin, or whatever you have and just navigate to it and see what is in there. If it is identical to the content of /dev/sda6 then that is your phantom partition and you can probably safely delete it, but if it is something that you have plugged in and would rather like to keep then leave it alone.

So let me run it by you again, don't delete anything unless you know what it contains and you are sure you don't want it.

Caveat Emptor!!

---

