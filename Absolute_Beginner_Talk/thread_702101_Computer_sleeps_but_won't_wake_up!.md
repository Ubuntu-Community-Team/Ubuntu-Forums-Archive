---
title: "Computer sleeps but won't wake up!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by bw44 on 2008-02-19
I checked other threads with similar titles, but no joy.  The most recent was dropped almost a year ago with no resolution.

I recently got  a Compaq (HP) Presario laptop and Ubuntu Gutsy is installed and working fine, but for the first time it went to sleep (while on AC power).  I had changed the setting "Put computer to sleep when inactive for" from "never" to "30 minutes" to test it.

After it suspended,  the power button light was flashing and I followed the owner manual's instructions (which I know assume you're running Windows!) and pressed it.  Nothing happened. Was this a mistake?  All that was showing on the screen was "Linu" in yellow letters in the upper left with a flashing cursor.  I had to unplug the computer and take the battery pack out to get it to reboot.

In one of the earlier threads someone suggested:> try adding resume=/dev/xxxx to the kernel line in your /boot/grub/menu.lst (with resume=/dev/xxxx replaced by your swap partition reference)

It did not work for the person who started the previous thread, but should I try it? Is there something else I should check first?

I also noticed that when I right click on the battery icon in the top panel it doesn't list "Hibernate" or "Suspend" as options.  Another article I read  at [http://spidertools.com/ub_power.php](http://spidertools.com/ub_power.php) showed those options on the drop down menu.  Should they be there? [Edit: Duh! Ignore this paragraph -- the options are there when I left click!]

Any help would be much appreciated!

---

### Post by firestormx37 on 2008-02-19
I have spent hours trying to get suspend to work correctly on my HP laptop, but have had not success.  I have experienced the problem in both Feisty and Gusty.  At this point, I have just given up on the suspend function and hope that it is fixed in later versions.  If you do happen to find something that works, then please let me know.  Otherwise, good luck.  This is a known bug that many people have trouble with.  Some people are able to tweak some settings and get it working, but I have had no luck with any of them.

---

### Post by bw44 on 2008-02-20
> **firestormx37 said:**
> I have spent hours trying to get suspend to work correctly on my HP laptop, but have had not success.  I have experienced the problem in both Feisty and Gusty.  At this point, I have just given up on the suspend function and hope that it is fixed in later versions.  If you do happen to find something that works, then please let me know.  Otherwise, good luck.  This is a known bug that many people have trouble with.  Some people are able to tweak some settings and get it working, but I have had no luck with any of them.Wow!  That's not encouraging, but I really appreciate your replying so quickly and letting me know it's a known and generally unresolved problem.

I assume you'll stay tuned to this thread for a little while, but if someone posts a solution or I figure anything out myself (unlikely!) I'll send you a private message.

bw44

---

### Post by hardyn on 2008-02-20
how big is the swap partition in relation to your physical memory size?

---

### Post by nsimeone2000 on 2008-02-20
I know this won't exactly fix your problem, but it may help someone with the same issue, I recently found out that every time I close my lid on my laptop that my computer freezes up, if I go outside and smoke a cigarette, my computer freezes up.  I just went into the power settings and made it so my computer does nothing when the lid is closed, and does nothing when idle.

So if you don't necessarily care so much about the sleep, but are irritated its freezing up, maybe this will help.

---

### Post by bw44 on 2008-02-20
> **hardyn said:**
> how big is the swap partition in relation to your physical memory size?

The swap partition size is 1.42 GB and physical memory is 500MB..

What about adding resume=/dev/sda5 (the swap partition)  to the boot kernel line?

---

### Post by bw44 on 2008-02-20
> **nsimeone2000 said:**
> I know this won't exactly fix your problem, but it may help someone with the same issue, I recently found out that every time I close my lid on my laptop that my computer freezes up, if I go outside and smoke a cigarette, my computer freezes up.  I just went into the power settings and made it so my computer does nothing when the lid is closed, and does nothing when idle.

So if you don't necessarily care so much about the sleep, but are irritated its freezing up, maybe this will help.Thanks for the tip.  I don't have a problem with closing the lid since I just tell it to blank the screen, not suspend or hibernate.  I don't really care about the system always running when on AC power, but I'd like to prolong the time I can use it on the battery. And  I figure if suspend doesn't work on AC it won't work on battery either.  No?

bw44

---

### Post by hardyn on 2008-02-20
okey... post the specs of you machine

I have had trouble with both the ATI and Nividia drivers, and it was resolved by adding vga=791 to the grub boot string.

---

### Post by nsimeone2000 on 2008-02-20
You are correct.

---

### Post by bw44 on 2008-02-20
> **hardyn said:**
> okey... post the specs of you machine

I have had trouble with both the ATI and Nividia drivers, and it was resolved by adding vga=791 to the grub boot string. Sorry, but what are they, and what's the quickest way to capture the specs you need  to see?  The video driver is "intel" (recently upgraded from 801d, I think).

I saw in one of your posts to another thread the recommendation to add vga=791 to the grub boot string do you think I should try that  and/or the resume=/dev/sda5, or wait until you've seen the "specs?"

Thanks for the help.

---

### Post by bw44 on 2008-02-20
> **nsimeone2000 said:**
> You are correct.

:)

---

### Post by hardyn on 2008-02-20
Go ahead and try the resume=.  It is not something i have ever had to do, but it is likely forcing the destination of the ram dump to disk, if for whatever reason it didn't happen correctly during install.

---

### Post by bw44 on 2008-02-20
> **hardyn said:**
> Go ahead and try the resume=.  It is not something i have ever had to do, but it is likely forcing the destination of the ram dump to disk, if for whatever reason it didn't happen correctly during install.Tried, but it made no difference at all.

Since I last posted, I read this comment by Matthew Garrett, who I think is head of the Ubuntu laptop team: [http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html).

I'm a little confused, but is it necessary to set ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support to get Ubuntu to manage the sleep/wake process?  If I understood correctly, if you don't, then the process is managed by settings in BIOS (somehow).  I looked at the BIOS settings on my Compaq Presario but none said anything about power management. (In another thread someone said to try to change the power management BIOS settings.  I guess my PC isn't that advanced, but I should add that the sleep/wake process works OK under the dual-boot XP system.)

From what I read, if you enable laptop mode you have to be careful about other settings which cause the disk to start and stop more frequently.  

Comments? Suggestions?

Thanks.

bw44

---

### Post by littletinman on 2008-02-20
I've got an acer 5520 and when i suspend it, it won't wake up. Help would really be apreciated. Thanks.

---

### Post by bw44 on 2008-02-20
> **littletinman said:**
> I've got an acer 5520 and when i suspend it, it won't wake up. Help would really be apreciated. Thanks.

Stay tuned!  Hopefully, we can come up with a more general solution that will work with Compaqs, Acers and whatever.

bw44

---

### Post by hardyn on 2008-02-21
> **bw44 said:**
> Tried, but it made no difference at all.

Since I last posted, I read this comment by Matthew Garrett, who I think is head of the Ubuntu laptop team: [http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html).

I'm a little confused, but is it necessary to set ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support to get Ubuntu to manage the sleep/wake process?  If I understood correctly, if you don't, then the process is managed by settings in BIOS (somehow).  I looked at the BIOS settings on my Compaq Presario but none said anything about power management. (In another thread someone said to try to change the power management BIOS settings.  I guess my PC isn't that advanced, but I should add that the sleep/wake process works OK under the dual-boot XP system.)

From what I read, if you enable laptop mode you have to be careful about other settings which cause the disk to start and stop more frequently.  

Comments? Suggestions?

Thanks.

bw44


you have to enable laptop mode to get any kind of battery life out of the notebook, but i don't think that it is required for the syspend/hybernate.  and yes, the default hard disk spin down, is WAY to frequent in laptop mode, 15s. i believe... making this about 2min does the trick for me.

again, its not going to hurt anything if you try it... and you will probably want it in the end anyway.

---

### Post by bw44 on 2008-02-21
> **hardyn said:**
> you have to enable laptop mode to get any kind of battery life out of the notebook, but i don't think that it is required for the syspend/hybernate.  and yes, the default hard disk spin down, is WAY to frequent in laptop mode, 15s. i believe... making this about 2min does the trick for me.

again, its not going to hurt anything if you try it... and you will probably want it in the end anyway.

That's very helpful, thanks.  I'd started to wonder if the suspend function was related to the laptop battery-saving function or not, since the power-saving feature was implemented on my old desktop pc.

And thanks for the suggestion about disk spin down time.  To enable it and specify the time, I have to set the ENABLE_LAPTOP_MODE to "true" and use the hdparm command with the -S option, is that right?  Why was 2 minutes a good time in your case -- is it just a trade-off between convenience, economy and disk life?

PS. What was that thing about the boot-up vga setting you said elsewhere might help? Tnx.

---

### Post by bw44 on 2008-02-21
> **bw44 said:**
> Stay tuned!  Hopefully, we can come up with a more general solution that will work with Compaqs, Acers and whatever.

bw44I'm afraid I was being overly optimistic when I wrote this.  I didn't search the forums  using  the right terms, "suspend" and "hibernate."  There are many existing threads about problems with putting your system to sleep and waking it up.  I doubt there are any "general solutions" since it seems to be hardware dependent.

If I find a solution to my particular situation, I'll post the results here.  Thanks to hardyn and others who tried to help.

bw44

PS.  Will post future results to [http://ubuntuforums.org/showthread.php?t=698607](http://ubuntuforums.org/showthread.php?t=698607) which describes (better) a similar problem.

---

