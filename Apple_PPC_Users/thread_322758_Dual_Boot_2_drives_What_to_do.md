---
title: "Dual Boot 2 drives? What to do?"
date: 2006-12-20
forum: Apple PPC Users
---

### Post by st4rscream on 2006-12-20
OK My question is this I have a PPC Mac G3 300Mhz  I have osx on one harddrive and Xubuntu on the other but I want to be able to switch between the 2... I have had a bit of trouble here. If I install Xubuntu it works fine as does OS X, But I want both on 2 seperate drives. Can this be done? Everything I read is about  partitions. I don't want to reinstall OS X its an old version anyway now it seems after testing xubuntu os x isnt even loading.. Oh Woe is me.:confused:

---

### Post by st4rscream on 2006-12-20
OK it looks like as long as I dont have the linux drive plugged in mac OS X worrks.. but having to unplug the drive isn't exactly what I was hopinh for.

---

### Post by st4rscream on 2006-12-20
I feel silly posting to this.. ANY way it looks like it works only if I have 1 drive plugged in at a time.. what I have been doing is removing the power plug (inside the machine) from which ever HD I dont want. Anyway with the org mac one unplugged Xubuntu works.. if I unplug the linux drive mac os works.. Some one help to get these crazy kids to get along.

---

### Post by stream303 on 2006-12-21
If you hold down the **option / alt** key while booting, do you get the choice of which hard drive to boot from?

I'm not familiar with your G3, but this is how it works on my G5...

---

### Post by linear on 2006-12-21
I'm guessing you may need to roll your own yaboot.conf, putting in the correct paths to both drives and partitions. There's information [here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml").

---

