---
title: "Cpudyn vs. powernowd frequency scaling"
date: 2008-03-31
forum: Apple PPC Users
---

### Post by stream303 on 2008-03-31
Whaddya' know!  I just exchanged the default powernowd daemon for the cpudyn frequency scaling daemon, and I like cpudyn better on my G5 iMac with Gutsy.

I was playing around with Hardy Beta, and discovered that even though powernowd was installed, there wasn't any frequency scaling going on.  Thanks to somethingkindawierd, I uninstalled powernowd, and used cpudyn instead.  Great, my Hardy install is doing ok now.

I went back into my Gutsy install, and did the same thing.  I find that cpudyn is a bit more responsive, and provides a nice little boost since it doesn't seem quite as conservative as powernowd.

Awesome.  I can see it immediately with the cpu frequency-scaling applet added to the upper panel.

---

### Post by slacka-vt on 2008-04-02
stream303 thanks a bunch !
I installed cpudyn and removed powernowd and my
cpu efficiency has improved a noticeable amount.
Like you, I keep a close eye on my CPU monitor.
And, like you, I observed that with powernowd is was either "all or none".
Now with cpudyn, my CPU monitor has a lot more "peaks and valleys"
which indicates to me that cpu usage adjusts much more dynamically then before.
As a consequence, my fans are much more quite too.
I wonder why powernowd is installed by default ?
maybe cpudyn is too "bleeding edge"


BTW, I am on a PowerMac G5  Dual 2.7Ghz

~s

---

### Post by stream303 on 2008-04-03
I think powernowd is simpler to deal with from what I've read, but I'm no programmer, and it may be less ram hungry than cpudyn - although I haven't looked into it much.

I'll bet that if I do some digging I can find how to change the default settings in powernowd.

I like the response times for cpudyn as well.  Might be a keeper!

---

### Post by stream303 on 2008-04-05
Drat - the screaming fans are back on my G5 iMac with Hardy Beta - I'll be posting this issue there too in case any Ubuntu devs are subscribed via rss to the testing on ppc thread...

This is weird.  To get frequency scaling to work on Hardy, I had to use cpudyn as the scaling daemon.  What I discovered today was that if you don't log in and just leave the gdm login screen up, after about 5 minutes, the fans go ballistic again.  If you log in relatively quickly, no problems - fans are quiet and scaling is working.

If I use powernowd, everything is fine, even if the gdm login screen is left up for 5 minutes or more, but then I don't have any frequency scaling.

Off to the Hardy Development forum!

---

### Post by tomjennings on 2008-06-27
There is something odd with cpufreqd and Hardy.

I have a new (Feb 08) machine, built for low-latency audio, using mixxx (dj software) could not get the latency reliably below 40! ms! It exhibited typical slow/overloaded CPU problems (clicks, gapping, etc) yet powertop, top, etc showed the expected low usage.

At boot/gnome startup I woudl get the warning about "frequency scaling not supported". Well BFD -- it's a desktop I don't care,s o I ignored it.

Same problems with jackd, never got it to work with Hardy. I had it OK with feisty but there were other problems so I dropped it. Then uprgaded to hardy.

Without much to go on 'cept this thread, I removed cpufreqd and isntalled cpudyn. Aha! Mixx runs GREAT with 2 - 6mS (occasional click at 2, never at 6mS). That's an order of magnitude...

So before I wrote up a report, I figured I'm do a bit of regression. I rebooted (w/cpudyn in), still good w/4mS latency. apt-get remove cpudyn, install cpufreqd... Low latency still works fine. So it's not simply 'cpufreq bad, cpudyn good', there's something more subtle here.

Maybe the remove/reinstall "fixed something". I hate that. 

I will do the cpufreq/cpudyn install/remove reboot biz and if I get any ahrd correlation, I'll post here and open a bug if warrented.

---

### Post by stream303 on 2008-06-28
Interesting - thanks for the report!

Well, on my Hardy system, it looks like we're dealing with three things now: Powernowd (installed by default), CpuDyn, and CpuFreqd.

I just doublechecked and Cpufreqd was never installed - Only powernowd was installed by default.  Since that didn't work well, I removed powernowd, and even unchecked it from the System > Administration > Services options.  I then installed Cpudyn and all is good for the most part.

I'll have to see what's up with cpufreqd (vs cpudyn and powernowd) and see if there is anything there.

The biggest issue seems to be that with powernowd installed, it doesn't recognize any condition other than "performance", and with cpudyn, it only uses either "performance" or "power save" and completely misses "on-demand" :)

UPDATE:  I tried cpufreqd, and like powernowd, it stayed at performance level all the time.  Only cpudyn seems to work on my system.

I think the latency issues might be related to on-demand anyway - seems that when I did have powernowd working, it really had to be pushed hard to get "performance" level working, whereas with cpudyn, it will go there at the drop of a hat - since I believe it ignores on-demand.

I'm also wondering how latency settings that used to be recommended for pre-hardy kernels, now work with Hardy's "tickless" kernels, and also possible changes to the scheduler... I'm no kernel guru that's for sure.  Time to knock on stmiller's door!

---

