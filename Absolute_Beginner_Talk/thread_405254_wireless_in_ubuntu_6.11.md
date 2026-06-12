---
title: "wireless in ubuntu 6.11"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by nitsan on 2007-04-09
hi all,
I've installed ubuntu 4 days ago and it's working all fine except my wireless connection.
It seems like sometime it is connected to my home network and sometimes not.
I've downloaded wifi radar and kwifi and there I can see i'm connected to the my net, BUT :
1. How can I connect my net if I **didn't** entered my net Password ?
2. when I'm connected there are some sites I just can't get - google for example when other sites come up with no problems.

I must mention there are some times everything work just fine - can't tell you why.
I've tried now to give my computer static ip. still problem 2 remains.

thanks,

nitsan

------------------------------------------------------------

using dell inspiron 6000 with intel pro 2200BG network card.
works just fine with XP.

---

### Post by becominglumberg on 2007-04-09
In the thread here:
[http://ubuntuforums.org/showthread.php?t=399407&highlight=2200BG]("http://ubuntuforums.org/showthread.php?t=399407&highlight=2200BG")
it seems that all you need to do is install network-manager. Perhaps it is worth a look.

---

### Post by nitsan on 2007-04-20
well after few days i've come to a solution.
apparently my router won't communicate right with ubuntu so the ip and other data was not always transfered 
right from the router to the laptop.
configured it all manually (ip,dns,etc...) and it's working just fine now.

---

