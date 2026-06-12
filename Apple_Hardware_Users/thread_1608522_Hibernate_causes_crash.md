---
title: "Hibernate causes crash"
date: 2010-10-29
forum: Apple Hardware Users
---

### Post by WanderingOak on 2010-10-29
I just installed Lucid on an iMac 7,1, and everything is working well, except for hibernate. Whenever I tell my system to hibernate, it becomes completely unresponsive. Sometimes, I have to power the computer down myself and reboot. However, occasionally, the computer displays the following error message then shuts down by itself

> [29722.336335] btusb_inter_complete: hci0 urb ffff88--6f4ec540 failed to resubmit
(1)
[29722.337323] btusb_bulk_complete: hci0 urb ffff88--6f4ec240 failed to resubmit
(1)
[29722.338322 btusb_bulk_complete: hci0 urb ffff88--6f4ec600 failed to resubmit
(1)When the computer shuts down by itself, the only login option that I have in Linux is the account that I was in before the crash. So far nothing has been damaged in these crashes (except for network manager, which I replaced with wicd).

---

### Post by tpievila on 2010-11-22
I have the same problem on MacBook, though the hibernate works usually. I get three errors with different hex values, and then the machine just freezes. It never reboots on it's own, I have to power cycle the whole laptop. Haven't been able to find out why it does it, I don't even own any bluetooth devices.

---

### Post by tpievila on 2010-12-08
No one else has this problem? Maybe my motherboard's just broken (it's also thinking that I have an optical audio cable connected all the time, again).

---

### Post by earlf on 2011-07-08
I'm quite late here, but am curious:
WanderingOak or tpievila did you find any solutions to resolve this?

I have a similar issue with 10.04 32bit on a 5,1 iMac.

---

### Post by tpievila on 2011-07-12
> **earlf said:**
> I'm quite late here, but am curious:
WanderingOak or tpievila did you find any solutions to resolve this?

I have a similar issue with 10.04 32bit on a 5,1 iMac.

 Not really... I just try to avoid sleeping/hibernating as much as possible. It has gone better, though. Maybe only one time in five results in a lockup. Sometimes it also takes a LONG time to get to the unlock screen, longer than booting would take.

---

### Post by Neds Moar Salt on 2011-07-12
[https://help.ubuntu.com/community/MacBookPro5-5/Natty#Suspend](https://help.ubuntu.com/community/MacBookPro5-5/Natty#Suspend)

---

### Post by tpievila on 2011-07-13
Mine's a non pro Macbook, so the EFI update doesn't apply. Neither do nvidia drivers. But I'll try adding the sky2 line and see what happens.

---

### Post by earlf on 2011-07-15
Thanks for the update tpievila. 

I've noticed a few (2 out of the past 3) resuming from suspend attempts have worked, while others haven't. I am avoiding hibernation too though. 

@Needs Moar Salt, I'll check out adding the sky2 snippet.

---

### Post by tpievila on 2011-08-07
Seems like sky2 didn't have any effect on hibernate on non pro Macbook. Sometimes it wakes normally, sometimes it freezes and after a while fan goes on, sometimes it wakes into a kernel traceback, and sometimes it seems like it has frozen, but after a minute or two, the unlock screen is shown.

---

### Post by earlf on 2011-09-01
> **tpievila said:**
> Seems like sky2 didn't have any effect on hibernate on non pro Macbook. Sometimes it wakes normally, sometimes it freezes and after a while fan goes on, sometimes it wakes into a kernel traceback, and sometimes it seems like it has frozen, but after a minute or two, the unlock screen is shown.

strange. At least the unlock screen comes alive sometimes.

 The fix above helped me for a few weeks until my machine has stopped hibernating altogether. The machine is rapidly approach its end. Thus, I am accepting the lack of functionality and blaming the problems on its old age.

---

### Post by tpievila on 2011-09-02
Yeah... except mine works perfectly under OS X so the hardware can't be that bad.

---

