---
title: "Gazelle Pro 6, crashing &amp; freezing"
date: 2013-09-16
forum: Any Other OS
---

### Post by sderrick on 2013-09-16
I have a Gazp6 that just(yesterday and today) started crashing and freezing.  Its never done this before for the 2.5 years I've had it.
I'm running Mint, which I've run on it since the second day I received it.  Nothing new installed in the last week or so. 

It seemed like it was running hotter than usual, so I checked the fans.  I blew them out, but they were already pretty clean. No change in temp.

I looked in the syslog and see this happening

```
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978291] CPU2: Core temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978292] CPU6: Core temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978294] CPU1: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978297] CPU3: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978298] CPU4: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978300] CPU5: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978301] CPU7: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978302] CPU0: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978303] CPU6: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978312] CPU2: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979303] CPU2: Core temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979303] CPU6: Core temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979304] CPU7: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979305] CPU1: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979306] CPU3: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979307] CPU0: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979308] CPU5: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979309] CPU4: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979309] CPU6: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979315] CPU2: Package temperature/speed normal
Sep 16 13:00:45 scott-Gazelle-Professional kernel: [ 3899.540130] [Hardware Error]: Machine check events logged
```

The same second the kernel is reporting a temp above normal and throttling the cpu, it reports temp normal.  It just can't cool down that fast! 

And then there is the follow on [Hardware error]?  Is that referencing the over temp? Is that logged somewhere else? I've looked in /var/log and don't see anythign usefull.

This is my work machine and I've had it freeze 3 times and shut down twice today.  

ANy help woudl be appreciated!

Scott

---

### Post by Elfy on 2013-09-16
*Thread moved to **Other OS/Distro Support**.*

---

