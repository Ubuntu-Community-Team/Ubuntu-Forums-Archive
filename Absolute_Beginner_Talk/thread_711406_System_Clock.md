---
title: "System Clock"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Dave49 on 2008-02-29
I have Windows XP Pro on one drive caddy. I have Ubuntu on another caddy. My Ubuntu OS shows the correct time. I have it set to sync with internet time. Yet when I shut down my computer, remove the Ubuntu caddy, and insert the XP caddy and boot into XP, the time jumps ahead 5 hours. What would cause this?

~Dave :confused:

---

### Post by kebes on 2008-02-29
It's a time-zone error.

This occurs in dual-booting because Linux assumes that the system clock is set to UTC, whereas Windows assumes the system clock is set to local time. The 5-hour difference is the difference between your local timezone and universal time.

There are various ways of fixing it. I think the easiest is, in Ubuntu, change the date/time settings for the clock. There is an option where you can switch between using UTC vs. Local Time. Set it to local and it should work.

More info [here]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde").

---

### Post by kinghowdy on 2008-02-29
This has happened to me before. I assume you live in the Eastern Time Zone (b/c it is UTC -5 hrs). Make sure in Ubuntu and Windows that your time zone is set as Eastern. Then make sure the time syncs correctly. What I believe to be happening is that the system clock is syncing to show the correct time. However since your time zone is set incorrectly it resets the BIOS clock. Then Windows jumps ahead 5 hours.

---

### Post by Dave49 on 2008-02-29
My time zone is set correctly for Eastern U.S. I will have to check the UTC/Local Time thing next time I boot the Ubuntu caddy.

Thanks very much guys.

~Dave

---

### Post by Dave49 on 2008-03-01
My time zone is set to New York, which is my time zone. UTC is not ticked. The correct time and date is shown on the upper bar. But when I shut down and switch to my XP caddy, the date goes back to GMT in the BIOS. How can it be this difficult?

~Dave

---

### Post by kebes on 2008-03-01
The procedure that worked for me is described [here]("http://ubuntuforums.org/showpost.php?p=3711442&postcount=3").

[This  page]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde") (at the bottom) describes a procedure for making sure both Windows and Ubuntu use UTC (I've never tried it, though).

---

### Post by Dave49 on 2008-03-01
> **kebes said:**
> The procedure that worked for me is described [here]("http://ubuntuforums.org/showpost.php?p=3711442&postcount=3").

[This  page]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde") (at the bottom) describes a procedure for making sure both Windows and Ubuntu use UTC (I've never tried it, though).

But your last post to this thread tells me NOT to use UTC time. Now you are telling me to use it? I have not seen any way to set Windows to UTC time, anyway.

~Dave

---

### Post by kebes on 2008-03-02
> **Dave49 said:**
> But your last post to this thread tells me NOT to use UTC time. Now you are telling me to use it? I have not seen any way to set Windows to UTC time, anyway.

Like I said, there are many different ways to fix it (assuming I'm right about what the problem is). The easiest is to change the date/time settings in Ubuntu to be "local time" instead of "UTC."

If that doesn't work, then you can use force Ubuntu to use local time by editing the file "/etc/default/rcS" and setting "UTC=no". Or you can use the procedure I describe [here]("http://ubuntuforums.org/showpost.php?p=3711442&postcount=3") to manually force Ubuntu to use local time.



If none of that works, you can try the opposite strategy, described [here]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde"), which is to force Windows to use UTC. I've never tried it but it should work.

---

### Post by Dave49 on 2008-03-02
> **kebes said:**
> Like I said, there are many different ways to fix it (assuming I'm right about what the problem is). The easiest is to change the date/time settings in Ubuntu to be "local time" instead of "UTC."

If that doesn't work, then you can use force Ubuntu to use local time by editing the file "/etc/default/rcS" and setting "UTC=no". Or you can use the procedure I describe [here]("http://ubuntuforums.org/showpost.php?p=3711442&postcount=3") to manually force Ubuntu to use local time.



If none of that works, you can try the opposite strategy, described [here]("https://help.ubuntu.com/community/UbuntuTime#head-31a2e864837bce9761bc0520026f78970d18afde"), which is to force Windows to use UTC. I've never tried it but it should work.

Thanks for the clarification. That's the first thing I will try next time I boot Ubuntu.

~Dave

---

### Post by Dave49 on 2008-03-02
Ok, I went to gedit/etc/default/rcS and it said "Bash No such file or directory" 

~Dave

---

### Post by kebes on 2008-03-02
> **Dave49 said:**
> Ok, I went to gedit/etc/default/rcS and it said "Bash No such file or directory" 

I'm assuming that the typo you made above (missing space), you didn't make when issuing the command. It should be:
```
gksudo gedit /etc/default/rcS
```
(a space between gedit and the path) It would be strange if that file didn't exist (it exists on my Ubuntu 6.06/Dapper and Ubuntu 7.10/Gutsy installs). Still, if that file is completely absent, I think you can safely create a new text file that just contains the line "UTC=no".

Or try one of the other methods.

---

### Post by Dave49 on 2008-03-02
Yes, I am a beginner in the most complete sense of the word. Thanks for the command line. Until I get on to forming these lines, I will be grateful for as many as I can get in explanations of this nature. I will try again a little later with your command line in place of mine.

Thanks,

~Dave

---

