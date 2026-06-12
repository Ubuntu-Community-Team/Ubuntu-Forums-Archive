---
title: "Screen freezes can't reboot"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-09-03
I have been having a recurring problem with the screen freezing.  I'm not able to do anything including a restart.  When I power down and restart I am sometimes able to resume but lately I haven't.  I get up to the splash screen and then I see the following:

[I]Mount: mounting/procon/root/proc failed;no such file or directory

Target file system doesn't have/sbin/init[/I]

Another time I received this:

[I]Busy box v1.1.3 built-in shell (ash
/bin/sh can't access tty; job control turned off[/I] 

I also see something about Timidity.  * Timidity is not yet configured*

Is this hopeless?

---

### Post by Harpoon on 2007-09-03
I certainly don't clain enough expertise to exp;ain the why's of your problems, but I did some searching and found this relating to the busybox error:
[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)
procom is a mozilla extension (plugin) that may have installed improperly.  If the above link gets you booted up, you might consider uninstalling the plugin for a bit to see what, if anything, turns up.  If you seem good to go, then reinstall it.

You are not the only one who has had this problem. But saying misery loves company is not going to help, so I won't say it.  Good luck

---

### Post by djen9999 on 2007-09-03
Thanks for your reply.  I'm not sure if this is the cause of the main problem but I will certainly try.  Thanks!

---

### Post by Yizi on 2007-09-03
It can be your hardware problem i asumme it's a fan problem, open you case make sure all the fans working specialy the CPU fan.

**Reason: When fan stops working the machine gets to hot if stays like that you loose your hardware so the system freezes itself.**

*I recommend you add a extra fan incase ;)*

---

### Post by djen9999 on 2007-09-03
I actually have a high end power supply and a high end fan.  I know the fan is working because this thing sounds like a 747 coming in for a landing.  :)

---

### Post by Yizi on 2007-09-03
> **djen9999 said:**
> I actually have a high end power supply and a high end fan.  I know the fan is working because this thing sounds like a 747 coming in for a landing.  :)

In that case OK then, nice PC though :D

---

### Post by djen9999 on 2007-09-03
I tried the link, Harpoon but the easy method didn't work and the technical method is way beyond me.  BTW it was PROCON not PROCOM in the error message.  I only have a few Mozilla add-ons and that didn't soudn familiar.  Thanks for the effort.

I'm quickly coming to the belief that this is a hardware problem.:confused:

Anyone else?

---

### Post by djen9999 on 2007-09-03
Two questions.  The light for my hard drive now stays on constantly.  One reason I'm guessing it's a hardware problem.  Is this a correct assumption?

I'm thinking of getting an external hard drive.  What do I need to know about booting using such a device?  My BIOS does have provisions for for booting from an external device.

---

### Post by Yizi on 2007-09-03
> **djen9999 said:**
> Two questions.  The light for my hard drive now stays on constantly.  One reason I'm guessing it's a hardware problem.  Is this a correct assumption?

I'm thinking of getting an external hard drive.  What do I need to know about booting using such a device?  My BIOS does have provisions for for booting from an external device.

I told you it's a hardware problem, i think it's possible to boot from a external, i have seen others doing it but never done it myself. I think others should be able to help you on this.

---

