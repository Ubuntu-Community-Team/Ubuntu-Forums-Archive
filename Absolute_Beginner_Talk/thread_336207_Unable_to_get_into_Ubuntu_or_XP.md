---
title: "Unable to get into Ubuntu or XP"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2007-01-11
Hi,
I have been having problems lately getting into Ubuntu or XP after having no problems for a month or better.
When I turn the computer on it goes and sounds normal until it is supposed to reach Grub and then freezes. Let me try to be a little clearer here.
1. for about a week before this happened one of the hard drives was running constantly (the hard drive light was on all the time. I thought that there could be a virus or spyware (on win xp sp2) so I ran zone alarm virus checker and spyware with negative results. I then ran adaware and again negative results. I ran check disk on the 'c' drive and no problems found.

2. Just before the above happened  I tried to load  Ubuntu (6.06 dapper) and it froze at the second step (loading root or something) and when I restarted the computer I was able to get in and shut down normally.

3. Now it is a hit and miss situation where sometime I can get into grub and others I can't. I am wondering if the MBR is corrupt. I don't know what to do and I afraid that I am going to lose my computer. I don't have anything backed up because I was saving to buy an external back up drive.

I have the following:
Intel Pent. 3 with an 866 chip set
512 ram
60 GB hard drive where Win XP pro sp2 reside
40 GB hard drive where Ubuntu 6.06 dapper resides.
I believe that Grub resides on my 'c' drive because when I installed Ubuntu I allowed it to install in the default location.

I am afraid to shut my computer off now because I may not be able to start it again but I will shut it down tonight because of the weird weather we are having and I could lose power.

Thank You,
Carolyn

---

### Post by Sef on 2007-01-11
> I am wondering if the MBR is corrupt.

If it is that, then read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by Sunflower1970 on 2007-01-11
Could one of the hard drives be going out?

---

### Post by ieee488 on 2007-01-11
Back up your data to a DVD or a couple of CDs.
Your photos and Word files etc

It is a pain in the butt to have to do this, but I agree it sounds like one of your hard drives can be going bad.

---

### Post by confused57 on 2007-01-11
You can install grub using the live cd:
[http://ubuntuforums.org/?t=224351](http://ubuntuforums.org/?t=224351)

Also, if you're booted into Ubuntu when you notice your hard drive light staying on, open a terminal and enter:
```
top
```

see if a program is consuming too much of your CPU...if it is, there is a PID number to the left of the offending program, press ctrl+c to exit top, then at the prompt, enter:
```
kill -9 <PID#>
```

e.g.  kill -9 4515

This probably has nothing to do with your grub problems, but "may" explain your hard drive light staying on...or as Sunflower mentioned, may be a problem with your HD.

---

### Post by tagginannie on 2007-01-11
> **Carolyn62 said:**
> Hi,
I have been having problems lately getting into Ubuntu or XP after having no problems for a month or better.
When I turn the computer on it goes and sounds normal until it is supposed to reach Grub and then freezes. Let me try to be a little clearer here.
1. for about a week before this happened one of the hard drives was running constantly (the hard drive light was on all the time. I thought that there could be a virus or spyware (on win xp sp2) so I ran zone alarm virus checker and spyware with negative results. I then ran adaware and again negative results. I ran check disk on the 'c' drive and no problems found.

2. Just before the above happened  I tried to load  Ubuntu (6.06 dapper) and it froze at the second step (loading root or something) and when I restarted the computer I was able to get in and shut down normally.

3. Now it is a hit and miss situation where sometime I can get into grub and others I can't. I am wondering if the MBR is corrupt. I don't know what to do and I afraid that I am going to lose my computer. I don't have anything backed up because I was saving to buy an external back up drive.

I have the following:
Intel Pent. 3 with an 866 chip set
512 ram
60 GB hard drive where Win XP pro sp2 reside
40 GB hard drive where Ubuntu 6.06 dapper resides.
I believe that Grub resides on my 'c' drive because when I installed Ubuntu I allowed it to install in the default location.

I am afraid to shut my computer off now because I may not be able to start it again but I will shut it down tonight because of the weird weather we are having and I could lose power.

Thank You,
Carolyn


Hi Carolyn :-)

So glad to see another girl hear :-) This thread might help you 

[http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")


Suzy

---

