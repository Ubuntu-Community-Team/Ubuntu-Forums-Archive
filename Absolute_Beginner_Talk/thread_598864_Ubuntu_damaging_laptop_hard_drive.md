---
title: "Ubuntu damaging laptop hard drive"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-10-31
Hi
recently i was reading articles on digg.com.I found one article regarding ubuntu bug which is damaging your hard drive see this
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

well what ya guys think about this?I am new in ubuntu world and using it on laptop from feisty and now running gutsy?

---

### Post by ThrobbingBrain66 on 2007-10-31
It's been covered ad nauseum here on the forums...you'll find 100's of threads (maybe a slight exageration) if you do a search.  The problem is NOT Ubuntu.  Windows handles power management settings exactly the same way, but I don't see anyone putting blame on Microsoft.  It's pure FUD.

I'll follow up with some links when I find them.

EDIT:

[http://ubuntuforums.org/showthread.php?t=598731](http://ubuntuforums.org/showthread.php?t=598731)
[http://ubuntuforums.org/showthread.php?t=596602](http://ubuntuforums.org/showthread.php?t=596602)
[http://ubuntuforums.org/showthread.php?t=566072](http://ubuntuforums.org/showthread.php?t=566072)

---

### Post by poision_heart on 2007-10-31
Oh yeah i ve been through those threads.There is no proof that ubuntu damaged hard drive.Overall we can say that rant is totally false am i right?

---

### Post by oilchangeguy on 2007-10-31
> **poision_heart said:**
> Oh yeah i ve been through those threads.There is no proof that ubuntu damaged hard drive.Overall we can say that rant is totally false am i right?

this is false. software is not capable of doing physical damage to hardware. this does not include something like a virus damaging files. but that would be software, damaging software. somewhere somebody had a hard drive die, and of course blamed it on the operating system.

---

### Post by ThrobbingBrain66 on 2007-10-31
> **poision_heart said:**
> Oh yeah i ve been through those threads.There is no proof that ubuntu damaged hard drive.Overall we can say that rant is totally false am i right?

I think so.  Being the top dog has it's advantages and disadvantages.  On one hand Ubuntu gets praised for taking Linux to places it's never been.  On the other, people will take any opportunity to lay blame for anything they can think of.

---

### Post by pgmer6809 on 2007-12-26
It is not total FUD. The s/w does not damage the hard drive per se. What Ubuntu does (and maybe other distros also) is access the hard drive at least once per minute. Even if the machine hasn't been touched for hours, chunk, chunk, chunk, once per minute.
Since any given hard drive only has so many cycles of life, this MAY have the effect of increasing the wear and shortnening the life of the hard drive.

This issue has been around at least since FEISTY (dont think it existed in DRAKE), and nobody in the Ubuntu community seems to be able to answer WHY the disk needs to be accessed and how to turn off whatever demon/service is doing this.

One workaround seems to be to use hdparm to disable power management on the drive. However this just leaves it spinning, it does not address the root cause.

For the record Windows 98 does NOT do this. If you leave W98 alone, and dont touch it, the disk drives stay quiet.

I sure wish I could figure out how to stop this. For the momment it is the one thing preventing me from using Ubuntu regularly.

Note that this issue is not unique to laptops. Desktops have it too.

pgmer6809

---

### Post by RomeReactor on 2007-12-26
Hi. This is more of a problem of certain hardware manufacturers loading [aggressive settings on their HDs]("http://hardware.slashdot.org/comments.pl?sid=344745&cid=21175473"); these [two]("https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/10") [variants]("https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14") of the same solution may help with reducing disk access. Here's more [information on that]("https://wiki.ubuntu.com/DanielHahler/Bug59695").

---

