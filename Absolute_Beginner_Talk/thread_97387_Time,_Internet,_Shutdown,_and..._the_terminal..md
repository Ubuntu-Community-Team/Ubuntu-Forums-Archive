---
title: "Time, Internet, Shutdown, and... the terminal."
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by sonyacarlson on 2005-11-30
I am trying to get into Linux because it is different and FREE.  I had the 4.10 version sent to me on CD and I just installed it today.  Now I see there have been 2 newer versions, but oh, well.

I say the install went quite well.  I am not scared to do new stuff with the computer.  I have learned how to install parts--drives & memory--in the last year.  I made the switch to Firefox last year and haven't looked back.  I also have Thunderbird on my XP laptop.  

So, a friend gave me an extra computer that had Win98 on it.  I figured instead of paying to put XP on an older machine, I would fiddle around with Linux.  I am just confused where to put in the codes that people have suggested.   I installed Ubuntu just fine and the computer starts, it has open office and firefox and evolution BUT:

I have 3 problems I can't fix:
1.  I can't onto the internet--I get a message when I log on that the etc/host is wrong (or something to that effect).  I search on the board and saw some suggestions how to fix this, but not where to ping or write in the code.  Where do I ping?

2.  I can't change the time on the computer.  I am in the Eastern Time Zone and the computer knows that.  BUt the clock is 6 hours slow.  The change time and date button doesn't bring up anything to change.

3.  When I shutdown, the screen says it shutdown, but the computer doesn't turn off.

Again, I am willing to type in code places, I am just totally lost where to type code.  Or ping stuff.  Or anything.  I have been trying to surf this forum but I can't find out where I change stuff.

Please advise!
Thanks!  Sonya

---

### Post by aysiu on 2005-11-30
[QUOTE=sonyacarlson]I am trying to get into Linux because it is different and FREE.  I had the 4.10 version sent to me on CD and I just installed it today.  Now I see there have been 2 newer versions, but oh, well.[/quote] You can upgrade to the newest version (5.10)... uh, once your internet is working, of course.

> 
I am just confused where to put in the codes that people have suggested. I haven't used 4.10, but in 5.04, the terminal was in Applications > System Tools > Terminal.

> 1.  I can't onto the internet--I get a message when I log on that the etc/host is wrong (or something to that effect).  I search on the board and saw some suggestions how to fix this, but not where to ping or write in the code.  Where do I ping? What kind of internet connection should you have? Broadband? Dial-up? Most of the time, going to System > Administration > Networking and choosing to have Eth0 be DHCP works for broadband connections.

> 
2.  I can't change the time on the computer.  I am in the Eastern Time Zone and the computer knows that.  BUt the clock is 6 hours slow.  The change time and date button doesn't bring up anything to change. Did you select to use UTC during installation? If so, that could be your problem. Or, if you're not dual booting, choosing not to use UTC may be your problem. Do you remember anything about being asked about UTC and Greenwich Mean Time?

> 
3.  When I shutdown, the screen says it shutdown, but the computer doesn't turn off. What about if you shut down from the terminal ```
sudo shutdown -h now
``` Still no go?

---

