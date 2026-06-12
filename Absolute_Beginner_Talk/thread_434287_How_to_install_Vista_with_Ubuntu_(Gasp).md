---
title: "How to install Vista with Ubuntu (Gasp)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jolzath on 2007-05-05
I need to install Vista (Its the only Windows CD I have, recovery eats Ubuntu, and then Grub won't let me run the recovered XP Media Center Ed.) So I am wondering how am I able to install my free Vista (Promotional for buying an Acer Aspire 5600) without it eating Ubuntu, assume I know very little about GRUB (Almost none, cept' it I can somehow use it to choose OSes), and Unix commands.

Note: I need to have Vista on, so the teachers will let me plug into the School's Internet. They are afraid that since I have Linux I am some kind of super security cracker trying to take over the school. No joking either.

---

### Post by starcraft.man on 2007-05-05
> **Jolzath said:**
> I need to install Vista (Its the only Windows CD I have, recovery eats Ubuntu, and then Grub won't let me run the recovered XP Media Center Ed.) So I am wondering how am I able to install my free Vista (Promotional for buying an Acer Aspire 5600) without it eating Ubuntu, assume I know very little about GRUB (Almost none, cept' it I can somehow use it to choose OSes), and Unix commands.

Note: I need to have Vista on, so the teachers will let me plug into the School's Internet. They are afraid that since I have Linux I am some kind of super security cracker trying to take over the school. No joking either.

Quickest easiest way is to just resize your Ubuntu partition so you leave vista 20 GB or so I imagine. (Live Gparted cd can be got [here]("http://gparted.sourceforge.net/livecd.php")). After doing that, you will have to insert the Vista DVD and install it in the space only, make sure you manually point it to that 20 GB drive only. Then vista will install itself to the MBR, then all you have to do is restore the GRUB bootloader. Thats easily done, I believe ya want to read this [page]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") you'll need the alternate CD to follow it exactly, but I think the live cd is capable of restoring grub in almost the same way. Pay attention to the GRUB page closely, you don't wanna be stuck with a PC that can't boot either :p

That should do it :)

Just a note, but your school is truly ignorant to believe that you are some hacker solely on the basis of you choosing another OS. Is this your IT department telling you this? (I REALLY hope not...)

---

### Post by Jolzath on 2007-05-05
No, he actualy wants linux to be the OS for the school system...its the teachers who have no idea about computers, minus how to operate the system chancery enough for there own use...

---

### Post by crimesaucer on 2007-05-05
Or try this page (all though it says it's for 6.06 and Vista beta, but it shouldn't be that different?) : [http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

or this looks like a good page to read: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

...those were recommended from here: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

...and the home page link of that guide for more info: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by darkrose on 2007-05-05
Theme your desktop to look like vista when you're at school, and see if they even notice.

---

### Post by tgalati4 on 2007-05-05
Skip school.

---

### Post by boudreaujr on 2007-05-06
I really had stupid people who are in charge of others.  I'm betting on the post about installing a vista theme and they wouldn't know the difference.  If they give you more flack you can always ask them if because they drive a car they must a drunk driver type analogy.  A little education is a hard thing to get across to someone like this.

> **Jolzath said:**
> Note: I need to have Vista on, so the teachers will let me plug into the School's Internet. They are afraid that since I have Linux I am some kind of super security cracker trying to take over the school. No joking either.

Best of luck.

Denis

---

