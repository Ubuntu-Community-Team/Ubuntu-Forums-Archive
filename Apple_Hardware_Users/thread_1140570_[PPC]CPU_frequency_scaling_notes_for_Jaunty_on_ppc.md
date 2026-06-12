---
title: "[PPC]CPU frequency scaling notes for Jaunty on ppc"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by stream303 on 2009-04-27
Just a note that I started testing with Jaunty when it was an RC, and neither powernowd or cpudyn cpu frequency scaling was installed by default.  I'm not sure if this has been changed in the actual release.

For many, this is a good thing allowing the user to decide if they want to run it.

If you decide to run with powernowd on ppc, the fix in the wiki still applies - after installation you need to edit the following file as root and comment out the following lines ##

**/etc/init.d/powernowd**

```
start() {
        log_begin_msg "Starting $DESC... "
#       if use_ondemand
#       then
#           log_end_msg 0
#           return 0
#       fi
        if check_kernel
        then
```

Or, you can use CPUDYN, which is not really suitable for smp machines, although it does have much lower latency when scaling up - might be good for anyone into multimedia on a single-cpu box.

cat /proc/cpuinfo can help tell you, or just add the gnome cpu-frequency-scaling applet to the top or bottom panel is a quick way to see it in action - there are a few others too.


Either one: Powernowd, Cpudyn, or none, take your pick. :)

**UPDATE** For some inexplicable reason, powernowd is stuck at full-throttle and nothing suspicious is showing in top.  Drat - back to cpudyn for me, which has never failed me....

---

