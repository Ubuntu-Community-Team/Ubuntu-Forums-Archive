---
title: "Swiftfox...not so swift."
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by seven7 on 2006-08-24
I've been having a field day trying to get firfox running a little quicker. So, I browsed a few threads and saw Swiftfox; so I gave it a try. Not too impressed. Heres the scoop: Centrino 760, 512mb RAM, Cable connection Internet, pages load like butt. I've tried all the tweaks in that other post. Is Ubuntu a resource hog...?...tell me Im wrong!! Cleanse these vile, god forsakened thoughts!!...

ps
- You all have been more than helpful. Thank you to those who actually take the time and help us Windows refugees.

---

### Post by TrendyDark on 2006-08-24
Have you given Opera a try? Opera is, by far, one of the fastest browsers out there.

---

### Post by seven7 on 2006-08-24
Ive tried Oper in XP. It was ok. With Opera will I need to install any additional plugins?

---

### Post by TrendyDark on 2006-08-24
Haha, You're going to think I'm automatix-man, but that's how I install Opera. Otherwise you have to do some really weird stuff to get Flash and such working (or so that's how it was last time I actually did all that manually).

---

### Post by morningblur on 2006-08-25
Something that made a noticable difference for me, was turning IPV6 off.

Unless you know the brand of router you're using actually utilizes this feature, usually it'll just slow things up.

Here is how: (from this topic: [http://ubuntuforums.org/showpost.php?p=1210481&postcount=4](http://ubuntuforums.org/showpost.php?p=1210481&postcount=4) )

> gksudo gedit /etc/modprobe.d/aliases

locate the line:

alias net-pf-10 ipv6

replace with the following line:

alias net-pf-10 off

That should hopefully do something for you.

---

