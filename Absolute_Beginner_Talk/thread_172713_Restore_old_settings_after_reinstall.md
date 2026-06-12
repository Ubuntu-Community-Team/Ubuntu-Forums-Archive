---
title: "Restore old settings after reinstall?"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-09
Hi,

I just reinstalled Ubuntu Breezy after trying to apt-get dist-upgrade to dapper. That whent totally wrong, so I decided to take a copy of my Home folder and reinstall.

I copied the old Home folder and overwrited the new one, but nothing seams to happend?

I want to restore my old settings, maybe I missunderstood this completely? Maybe thats not the way to do it?

---

### Post by adam.tropics on 2006-05-09
I had a similar problem when I tried to copy from Nautilus rather than terminal. It was a battle I ultimately lost! For the future I would suggest that keeping /home on a seperate partition solves this. Then if you ever reinstall,choose that partition to be mounted as /home, and choose to not formatthat partition, thereby keep the data. You will then have a fresh install with your /home (and most settings) intact.

---

### Post by aktiwers on 2006-05-09
Thanks

Should I then create a partion that is called

/home

Like the root is called

/

Or am I wrong again?

---

### Post by adam.tropics on 2006-05-09
Yes,exactly. However this solves future probelms rather than the current one, as you would still have to set everything up at least once more! But if you're installing fresh anyway, what the hell, go for it. On a side note, you will find many threads here about related to partitioning. Everyone has their own take on it really. In your case I would just suggest to make sure your newly created /home is large enough for your needs, and make sure in the install bit that it is set to mount at /home. (ps, for the first run at this you should really format all the newly created partitions, the 'keep the data' bit (previous post) only applies to future installs)

---

### Post by ncappel1 on 2006-05-09
I had the same problem you had too. if you are using nautilus remember that most of the settings are the hidden files. When you put those on a hard backup, like an external drive or cd/dvd make sure to copy (and then later, paste) all the hidden files too!

---

### Post by Cirrocco on 2006-05-09
/off topic

adam.tropics:

are you that guy from the ufo: aftershock forums who does that weapon rebalance mod thing?

---

### Post by adam.tropics on 2006-05-09
??   no, sorry!

---

### Post by Cirrocco on 2006-05-09
reason I asked: you two have the same avatar

check it:
[http://forum.ufo-aftermath.com//index.php?showtopic=1872]("http://forum.ufo-aftermath.com//index.php?showtopic=1872")

---

