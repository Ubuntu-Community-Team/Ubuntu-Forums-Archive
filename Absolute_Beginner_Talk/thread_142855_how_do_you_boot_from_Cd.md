---
title: "how do you boot from Cd?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by coolrunn on 2006-03-11
Have used search. no answer.

How do you boot from CD, i want to try the live ubuntu version Cd, but it don't work.

---

### Post by Klaidas on 2006-03-11
When you computer starts, press Delete button. BIOS will come up. There, set you computer to boot from a CD-ROM. 
Boot you windows, insert Ubuntu CD and restart. If you did everything correctly, it will boot the CD

---

### Post by kaamos on 2006-03-11
Hello!

First make sure you have burned the cd as an image. [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Then you have to make your computer boot from the cd instead of the hd. When you turn on your computer, there is usually some text like "press del to enter setup". Other common keys are F1 and F2. In the bios setup you should find something like "boot order" where you can set the primary device to boot from.

Hope this helps!

---

### Post by Xian on 2006-03-11
Read about the [Boot Device Selection](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch03s06.html#boot-dev-select).

---

### Post by bluevoodoo1 on 2006-03-11
Either you can go into your computer's BIOS and change the boot order to CD before HDD or there should be a button (one of the F# keys) you can push to boot from the CD from a list of drives. Yours will probably be different, but for me to get into BIOS it's the "delete" button and my select drive to boot from is F8. I like the second method better. As soon as you restart your computer begin tapping one of the buttons that you think it might be until a screen comes up.

---

### Post by Klaidas on 2006-03-11
Cool, now I know a new feature to do with the F# button :)

---

### Post by coolrunn on 2006-03-11
thanks for the help. It is an official ubuntu CD, which arrived in the post today by the way.

However I have done what you told me (configured my PC to boot from CD by 'striking' F12 on the start up screen.

HOWEVER I still can't get the ubuntu disc to load up all the way. The problem, i think, was that it couldn't install or whatever the Xgraphical interface display? 

I guess I should have noted down exactly what it said. But also I am wondering if my computer is compatible for this, after all it is a nice new DELL computer which had windows pre-installed. How long will it be before microsoft and its buddies manufacture hardware/software that disallows the installion of linux anyway.:-|

---

### Post by Q4U on 2006-03-11
Don't give up just yet: even if you pc does not play nicely with the default install, there are several different boot parameters which can be passed to overcome this.

You can also write down the error messages and post them on this forum. 

Q

---

