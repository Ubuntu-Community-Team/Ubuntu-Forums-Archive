---
title: "[SOLVED] controlling cpufreq"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by jpittack on 2007-09-21
from another thread, I decided to use cpufreq, based on the recommendations.  Now my laptop has the fan running on low non-stop.  When I open anything that would tax the cpu just a little more than normal browsing, the fan kicks into high and does not go back for a long time.

My battery life is around 1 hour and 30 minutes.  Under vista, I can easily get 3 hours 20 minutes. I also can't change the screen brightness like I can under vista (main problem with battery life)(fn+up/down).

Thus the question is, how do I first see what speed my cpu is at?  How do I change my cpu speed?  Is it possible to change the screen brightness?

---

### Post by agurk on 2007-09-22
In a terminal, type **cat /proc/cpuinfo** to see what your current speed is.
I haven't dabbled with adjusting my cpu speed, so can't help you there unfortunately.
Lastly, according to [this blog post](http://ubuntu1501.blogspot.com/2007/04/your-dell-1501-is-ready.html), regarding screen brightness:> The solution is to downgrade your bios to the 1.7.0 version.

---

### Post by PreviousN on 2007-09-22
the way i did it on my sony laptop:

Open a terminal and type:

sudo dpkg-reconfigure gnome-applets

It'll ask if you want to install the cpu throttler as suid root. Say yes.

Then, right click on whitespace on the bar on your desktop (it has "applications", "Places", "system" etc on it. Go "add to panel"

Then, choose from the list "cpu frequency scaling monitor". Click add. Close the window.

You should then be able to click on the frequency scaling monitor and from the drop down list choose the frequency you want to use....

---

### Post by jpittack on 2007-09-22
I can now see what the freqency is, and it has been running at 100% at all times.  sadly, I can not change the freqency with the drop down menu.  I get a little white dot in place of the menu.  The only complaint I ran in to was that it is unsupported.

---

### Post by bogolisk on 2007-09-22
> **jpittack said:**
> I can now see what the freqency is, and it has been running at 100% at all times.  sadly, I can not change the freqency with the drop down menu.  I get a little white dot in place of the menu.  The only complaint I ran in to was that it is unsupported.

I don't use laptop so I'm not sure what's avail on them but on my athlonX2 desktop, I use "ondemand" cpufreq governor. It's a in-kernel control so I don't have to worry about buggy userspace tools.

**cmdline method**
```

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
userspace powersave ondemand conservative performance
$ sudo sh -c 'echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor'

```

**gui method**
install the gfreqlet package. add it to the panel. use the gfreqlet applet menu to change governors or selecting speed.
[img]http://img101.mytextgraphics.com/photolava/2007/07/13/foo-1ieq163l.png[/img]

---

### Post by jpittack on 2007-09-28
using the cpu freqency scaling monitor that PreviousN suggested and resorting back to powernow (cpufreq was misconfiqured somehow), i now have a battery life around 2 hours.  
when i first checked the battery life, it told me a projected five hours.  a good lie but not as bad as the projected 19 hours that vista once gave me.
thanks for the info.  i am going to continue to play around with this, trying bogolisk's input, to see if cpufreq can give me more battery life.
I, like many, would like to switch entirely to ubuntu but am stilling waiting on some unresolved issues.  battery life is definately on my list, along with video and wireless.  of ofcourse game developers supporting linux is always a plus.

---

### Post by oliveroms on 2007-09-28
Hi,

I'm a happy gentoo user, but dualboot Ubunut ... just .. to see how other sdo it I suppose, to see how ubuntu is progressing, test stuff etc.

Also I use ubuntu completly 'user' mode. So I try finding solutions/answers in that sense.

That said, I also have installed the cpu applet, and reconfigured it (I suppose that's cheating, but dind't find a GUI way).

Initially I dind't get any governor or cpu speedstep support at all. I suppose it wasn't detected? (IBM T42, Intel Centrino Platform)

So i cheated again, and added acpi_cpufreq and cpufreq_ondemand etc to my modules list, and after restarting the applet, it all worked.

Thus my question is, why wasn't it properly autodeteted, and why isn't there an easy GUI way to add (pops up on google) other then to add it to the modules file? I haven't looked at one thing yet though, how to set the default governor, I assume/hope that the applet sets it to the last selected setting, if not i guess i'll ave to add it to my bootscript :/

Thanks,

Oliver

P.S. This ubuntu stuff is great sutffs :)

---

### Post by jpittack on 2007-09-29
I didn't have any functionality to start with.  The claim was that something was misconfiqured.  Mabye all of them need to be confiqured somehow?

My workaround was having powernow instead of cpufreq.

---

### Post by whitethorn on 2008-01-06
I got the cpufreq thingy working, but for some reason when I configure it in the terminal, after a while it changes all the configurations around.  So if I choose for it to run in conservative mode, I also have to tell it to start at 600 Mhz, and end at 1.5 Ghz. 
It'll run for awhile and then it'll change to performance mode, with 1.5 as being both the top and bottom levels.  I then once again have to reset it using the terminal...  Ne ideas how to get it, to just stay at the level I set it at?

---

### Post by jpittack on 2008-01-28
I was checking out my profile and ran across my old thread.

whitethorn, I have found a way to get this cpu applet working.  The command is sudo dpkg --reconfigure gnome applets following adding the applet.  This should allow the cpu applet to run as root.  Now the drop down menu works.  You can set what frequency you would like, or use the performance, ondemand, conservative and so on.

Drawbacks are that if you change it, it is not default.  It will go back to ondemand if you unplug the laptop, suspend, hibernate, restart, or shutdown.

I have been checking out saving battery life on my laptop, and changing from on demand doesn't help, and can hurt.  The reason for this are the energy states of the processor.  At 600 Mhz, it can have energy states of c0, c1, c2, and c3 or c4, if supported.  c0 draws the most energy, but you will not be able to see it through the applet or anything like that.  If you look at powertop, it gives you a rough idea about how many wakeups occur for the processor.  Mine wakes up 140 times per minutes, so at least 140 times in that minute, the processor steps up to c0 and processes information.  After it is done, it will return to a lower energy state.  If you use powersave, the processor stays at the same frequency, and thus takes longer to complete the task.  With ondemand, the task is finished faster, and the processor "races" to idle much faster, drawing more power to complete the task, but drawing less overall because of time spent in idle.

This may not be true for you.  I would try several settings, and measure the battery life that you get.  After I learned about all of this, I left my cpu at ondemand, and remove the applet, because it causes about 1 wakeup every ten seconds.  Not much, but I'm trying all I can to increase battery life.

Hope this helps!

---

