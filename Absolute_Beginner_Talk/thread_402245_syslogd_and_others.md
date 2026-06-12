---
title: "syslogd and others"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by DaDave on 2007-04-05
Is logging (klogd and syslogd) a necessary service on a home computer? Does it take up filespace? Are either of these logs good for tracking downloads/updates and where everything went?

Also in the services settings I notice that there are two of some services, like cupsys and hpli. Do I need both? I know I need cupsys.

The other two are anacron and atd. Do I need both? Either? 

Hahaha....sorry, guess I have been too immersed in linux/xubuntu for the last few days. Sure is a lot of stuff in there you can dig into, or dig up as the case may be.

---

### Post by kidders on 2007-04-05
Hi there,

> **DaDave said:**
> Is logging (klogd and syslogd) a necessary service on a home computer?I'm not sure how a Linux system would react if system logging were disabled. (Personally, I find it indispensable, so I've never considered trying it.) If space is precious, I suppose you could configure syslog not to write very much out to disk (default settings tend to be quite verbose), but I wouldn't really recommend  turning logging off altogether.

> **DaDave said:**
> Also in the services settings I notice that there are two of some services, like cupsys and hpli. Do I need both? I know I need cupsys. The other two are anacron and atd. Do I need both? Either? Those are questions only you can answer, really.

---

### Post by DaDave on 2007-04-06
> **kidders said:**
> Hi there,

I'm not sure how a Linux system would react if system logging were disabled. (Personally, I find it indispensable, so I've never considered trying it.) If space is precious, I suppose you could configure syslog not to write very much out to disk (default settings tend to be quite verbose), but I wouldn't really recommend  turning logging off altogether.

Those are questions only you can answer, really.

Well, it's true that only I can answer those questions, but I don't yet understand the purpose and function of those services. That's why I asked if they are necessary.

I have Mac (B&W G3) 350 Mhz, with a 6G hard drive. Yes, space is a little precious so I tend to watch it. So my questions remain, do I really need two of each of these services on a home computer?  Will removing one or both affect my computer? Is either of the syslogs good for tracking downloads(and where they where placed)? Cupsys I need, but do I also need hplip? Do I need both anacron and atd?

Until I services better I just need some advice as to which are really necessary to keep my computer running well.

Thanks - Dave

---

### Post by kidders on 2007-04-06
Sorry... I should really have been a little clearer in my last post![LIST]
[*]**klogd** - The kernel logger. On many systems, this function is fulfilled by **syslogd**, but there is a good argument that using a dedicated kernel log daemon is more efficient. Kernel messages are usually only important when something is misbehaving, or in the event of a serious fault ... under which circumstances the exact order & wording of reported errors is absolutely vital knowledge. Disabling the kernel log daemon would deny you that information.
[*]**syslogd** - A unified system logger, used in some manner or other (ie either directly or indirectly) by virtually every Linux application. Turning this off is of little benefit, but if space is precious, it can be configured to skip over unimportant messages, and only record things you're likely to be interested in. The best way to curtail disk usage by log files is to *increase* the degree to which your system uses **syslogd**, imo. Again, this service is really only useful when you're wondering "I'm missing some of my Gmail email... did procmail fetch it or not?" or "Why won't my USB device work today, when it was fine yesterday?" or "Ubuntu is spending a lot of time chatting with some guy on another continent ... when did he manage to get into my system, and what did he do?".
[*]**cupsys** - The Common Unix Print Service.
[*]**hpli** - A special service for HP printers. I deleted this from my systems, since I (thankfully) don't have any HP products.
[*]**anacron** - A system task scheduler. Disabling this can have serious adverse effects, since Linux would no longer be able to perform routine housekeeping tasks, much as OSX likes to do.
[*]**atd** - This daemon runs commands at some future time. If you were to disable this, you would have to be vigilant at all times, to ensure that nothing you're running looks like it might be relying on it.[/LIST]In most cases, disabling these services is of little benefit (carrying the possibility of major side-effects), and would result in a non-standard Ubuntu system. If you're good enough with Linux to intuit occasions where you might need to tread carefully, you can feel free to turn anything and everything off though.

Since you're a Mac user, you'll most likely be familiar with OSX. Quite often, apps (or system updates) you install make assumptions about your system that will only be invalid if you've played with something low-level. For example (and as you probably already know), installing APE, custom bootsplashes, tinkering with NVRAM, performing multi-partition installs, and so on can all trigger odd behaviour when you do something like install a QuickTime update, or an anti-virus utility. The questions you're asking about Linux are along a similar vein (and involve many daemons OSX likes to have running too). The point is though, that if you're experienced enough to handle any unpredictability you introduce, then there's no problem. :-)

To cut down on space wastage, I would suggest exploiting the system services you mention, rather than turning them off. For example, you could configure cron to empty trash cans, browser caches, thumbnail caches, delete installed .deb packages, remove temporary files, and so on, to help keep disk usage in check. 6GB is _very_ tight!

---

### Post by DaDave on 2007-04-06
Kidders - than you! This information is most helpful. I have so much to learn about linux.

I switched to xubuntu from OS 9.2. because I couldn't afford OSX (old retired guy) and I was very tired of being treated like an orphan because I didn't have OSX :) 

Anyhow, I really appreciate your help. At least now I have a place to start so now I am off to learn how to apply your suggestions. Thanks!

---

### Post by kidders on 2007-04-06
Yikes... sorry again! I guess trying to draw parallels with OSX wasn't terribly helpful of me. :-( (I was trying to draw on knowledge you may already have had.)

As Linux goes, Xubuntu is probably a little more of a jump in at the deep end than you may be comfortable with. It's interface is lightweight and simplified ... any time I use it, my terminal window simply never closes! Having said that, a G3 with so little room for manoeuvre (space-wise) may not enjoy running anything much more complex. (The motivation for your questions is becoming clearer all the time.)

If you get tired of Xfce, and decide not to even bother trying Gnome/KDE (for performance reasons), you might like to give Enlightenment a shot. I mention it because (a) info useful to users of low-spec machines can sometimes be difficult to come by these days, and (b) there is a special Ubuntu that seems to feature Enlightenment, out of the box.

> **DaDave said:**
> I was very tired of being treated like an orphan because I didn't have OSXI can imagine! Statistically, Mac users are fanatical upgraders. Steve really seems to give the cold shoulder to anyone who doesn't want to follow the crowd!

Anyhow, if you would like help on the specifics of any of my suggestions (or anything else), feel free to post back. Once you get to grips with things, and the learning curve starts to flatten a bit, you may also wish to consider kernel customisation as a way to squeeze more out of your G3.

---

### Post by DaDave on 2007-04-06
Kidders - I'm glad we had this chance to meet!

I haven't installed many (one?) extra program. Just running the way xubuntu came out of the box. So, disk space is no problem YET! I'm trying to save my pennies for a larger or extra drive  -  maybe the easter bunny or santa will help :o)

Thanks for the offer of help. I like to learn on my own when possible, and TIME is something I have a great deal of these days. 

Not to worry, Kidders, you will be hearing from me again! :lolflag:

---

