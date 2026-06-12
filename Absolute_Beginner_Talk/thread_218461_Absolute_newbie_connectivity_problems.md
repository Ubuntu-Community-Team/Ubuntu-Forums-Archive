---
title: "Absolute newbie connectivity problems"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by its_me_again on 2006-07-18
I've decided to take the plunge after years of putting it off and try linux.  I tried knoppix and dsl but both were just too difficult not having any in-depth guidance for a newbie like me.  I came across ubuntu and it seemed to have more support than the others (free ones anyway!), so this was for me I thought.  I'm pretty experienced around PCs - built my own machines, teach database techniques, all on windows of course.  Now I feel like the last 20 years were for nothing - I'm completely lost!

I loaded the live cd and the ubuntu desktop is incredible - easy enough to navigate and a remarkable array of programs.  However, despite searching the forums, guides wiki etc I can't get connected to my belkin router.  I have a belkin F5D7000 wireless nic which it seems isn't supported and have tried following the guides on installing the ndiswrapper.  I've tried several diferent methods but all fail.  I never got as far as loading the drivers and I know that I'm going to have problems as the cd drive isn't mounted and I can't get that to work either!  Surely if the drivers are on the (windows) c drive, I can access them there, can't I?

It's a brilliant exercise in humility and I hope someone out there is able to point me in the right direction.

Thanks in anticipation.

---

### Post by cyberlite on 2006-07-18
question: When you goto system the networking, do you see the card there????

---

### Post by its_me_again on 2006-07-18
No - there's nothing on network settings (except the modem connection).  I researched my nic and it's not supported.

---

### Post by Metacarpal on 2006-07-18
If you'd like to access your WinDriver to use ndiswrapper, you'll need to have your WinXP partition mounted.  Here's a helpful [help page]("https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html").

The CD-ROM drive doesn't mount until there's a readable disc in it.  Does it fail to mount when you put a CD in?

---

