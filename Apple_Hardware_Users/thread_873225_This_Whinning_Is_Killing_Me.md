---
title: "This Whinning Is Killing Me"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by DGortze380 on 2008-07-28
Help me out here guys, what actually works to get rid of this whine? 
I tried iSight 
I tried echo 2 > /sys/module/processor/parameters/max_cstate
Looks like 'Ubuntu Tweak 2.0' is supposed to work but I can't find it anywhere. What is it? Does it work? Where do I get it?

EDIT: on a fresh install of hardy

---

### Post by DGortze380 on 2008-07-28
ok, my temp solution is a simple shell script with an endless loop to keep a load on the CPU... but what other solutions are people using? There must be a batter way to stop this whine.

---

### Post by Raistlin82 on 2008-07-28
cant say as i have ever noticed a whine... could it be a hardware issue?  Do you dual boot and if so does it make any noise there?

---

### Post by DGortze380 on 2008-07-28
> **Raistlin82 said:**
> cant say as i have ever noticed a whine... could it be a hardware issue?  Do you dual boot and if so does it make any noise there?

It is document on the MacBook(1,1) although not all have the noise. Something to do with the CPU load while idle. 

It does do it in OS X, only after I've booted Ubuntu and only until I start a processor intensive application. 

I'm going to bring it to apple as soon as I can spare the computer for a week, but I'm positive they won't be able to replicate the problem because it will do it when I boot to show them, then not when their tech boots because OS X will be the last OS that booted at that point. (let me know if that makes any sense at all).

---

### Post by Raistlin82 on 2008-07-28
hmm sorry I dont know what to suggest with that... Will Apple tech support have an issue with you having installed linux I wonder. With some luck you'll get some help here soon, sorry I wasnt any use!

---

### Post by cyberdork33 on 2008-07-28
you have probably tried this already but have you reset the SMC?

---

### Post by kdb424 on 2008-07-29
Whining noise
In order to fix the whining noise that some MacBooks make, you need to install the iSight firmware. To install the iSight firmware, follow the steps listed below under "iSight". After installing the firmware and restarting, your MacBook should be whine-free.

Note: The above does not always work. In that case, add the following to /etc/init.d/acpid before exit 0.

echo 2 > /sys/module/processor/parameters/max_cstate
*Actually, this doesn't work ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206864)) apparently it is a kernel related issue, but there is a workaround, if you install Ubuntu Tweak 2.0 and you configure CPU Policy (Power Management) at PERFORMANCE it stops whining. I think it disables the C3 an C4 idle levels, but most important...it works.



[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)   <<< Check here if you want to read it better (it's in the FAQ topic at the top of the page [http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393))

---

### Post by DGortze380 on 2008-07-29
> **kdb424 said:**
> Whining noise
In order to fix the whining noise that some MacBooks make, you need to install the iSight firmware. To install the iSight firmware, follow the steps listed below under "iSight". After installing the firmware and restarting, your MacBook should be whine-free.

Note: The above does not always work. In that case, add the following to /etc/init.d/acpid before exit 0.

echo 2 > /sys/module/processor/parameters/max_cstate
*Actually, this doesn't work ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206864)) apparently it is a kernel related issue, but there is a workaround, if you install Ubuntu Tweak 2.0 and you configure CPU Policy (Power Management) at PERFORMANCE it stops whining. I think it disables the C3 an C4 idle levels, but most important...it works.



[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)   <<< Check here if you want to read it better (it's in the FAQ topic at the top of the page [http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393))

Already checked the FAQ, a number of times. I'm trying to find out what exactly Ubuntu Tweak 2.0 is and where to get it.

---

### Post by cyberdork33 on 2008-07-29
> **DGortze380 said:**
> Already checked the FAQ, a number of times. I'm trying to find out what exactly Ubuntu Tweak 2.0 is and where to get it.
I think they meant 0.2.0

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

I have never used the above, but it looks like just a general / miscellaneous settings-changer application. Looks interesting anyway.

---

### Post by DGortze380 on 2008-07-29
> **cyberdork33 said:**
> you have probably tried this already but have you reset the SMC?

I had reset the SMC about a year ago on an unrelated issue, I'll give it a shot and see if it does anything.

---

