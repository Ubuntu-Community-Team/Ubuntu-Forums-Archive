---
title: "strange issue home partition problem"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-01-09
I went and made a home partition on my latest Ubuntu install.  I followed all the steps on this site. [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I would just like to say that site is the bomb.  I have learned a lot from it.  I followed all the steps that it said to make a home partition without any problems.  SO I thought.  I deleted my backup home partition per instructions on the site.  But for some reason my system partition is still filling up too fast and I can not figure out why.  I have a 20 gig partition for programs.  So size should not be an issue.  But to be clear.  I do have A LOT of programs on my computer.  I have Studio Ubuntu and Kubuntu loaded on this system in addition to Gutsy Gnome.   Now here is the real strange thing.  I just enlarged the partition from 13 GIG to 20 because it filled up.  Then it filled up right away to 20 gig.....whats going on.  Why do I always get he weird stuff?  LOL

---

### Post by dcstar on 2008-01-09
> **nynoah said:**
> I went and made a home partition on my latest Ubuntu install.  I followed all the steps on this site. [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I would just like to say that site is the bomb.  I have learned a lot from it.  I followed all the steps that it said to make a home partition without any problems.  SO I thought.  I deleted my backup home partition per instructions on the site.  But for some reason my system partition is still filling up too fast and I can not figure out why.  I have a 20 gig partition for programs.  So size should not be an issue.  But to be clear.  I do have A LOT of programs on my computer.  I have Studio Ubuntu and Kubuntu loaded on this system in addition to Gutsy Gnome.   Now here is the real strange thing.  I just enlarged the partition from 13 GIG to 20 because it filled up.  Then it filled up right away to 20 gig.....whats going on.  Why do I always get he weird stuff?  LOL

If you system partition is filling up steadily then you are possibly filling it with log data, check your /var/log directory and see how big it is.

---

### Post by nynoah on 2008-01-09
what is the best way to do that?

---

### Post by nynoah on 2008-01-09
Well I opened it up, but I have no clue what I am looking for at all?

---

