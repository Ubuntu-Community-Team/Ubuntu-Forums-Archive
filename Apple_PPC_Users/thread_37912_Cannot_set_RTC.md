---
title: "Cannot set RTC?"
date: 2005-05-29
forum: Apple PPC Users
---

### Post by Slo Mo Snail on 2005-05-29
Hi,
I'm on a IBookG4 with the standard hoary kernel and every program trying to set the rtc gives the following error or something similiar (this is mplayer):

Linux RTC init error in ioctl (rtc_irqp_set 1024): Invalid argument
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.


The file in /proc does not exist... any ideas? manually invoking the ioctl results in the same error

---

### Post by Bob D. on 2005-05-29
Interesting, the file you mention in /proc *does* exist in the x86 version of Ubuntu, but this version (at least my copy), suffers from the same problem.Some apps (the Zapping TV Viewer in my case) need the RTC device set to 1024 and the command (apparently) isn't being accepted from the command in /proc.

At least for my issue, using the following command manually sets the RTC to 1024. Try it and see if it works for you. I got it from the tvtime website.

sudo sysctl -w dev.rtc.max-user-freq=1024

There must be a way to script this command to be run at startup time but I have no idea how to do it.

Let me know how it goes. Once I hear back from you, I'm going to file a bug against the x86 version...I'll let you do the PPC version. :)

Bob

---

### Post by timoor on 2005-06-30
[QUOTE=Bob D.]Interesting, the file you mention in /proc *does* exist in the x86 version of Ubuntu, but this version (at least my copy), suffers from the same problem.Some apps (the Zapping TV Viewer in my case) need the RTC device set to 1024 and the command (apparently) isn't being accepted from the command in /proc.

At least for my issue, using the following command manually sets the RTC to 1024. Try it and see if it works for you. I got it from the tvtime website.

sudo sysctl -w dev.rtc.max-user-freq=1024

There must be a way to script this command to be run at startup time but I have no idea how to do it.

Let me know how it goes. Once I hear back from you, I'm going to file a bug against the x86 version...I'll let you do the PPC version. :)

Bob[/QUOTE]
 Hi,
If you configure the kernel option to use the HPET (high precision event timer) the code in rtc.c will return
-EINVAL for this ioctl request - at least in 2.6.12. Hope this helps...
Tim

---

### Post by antidrugue on 2005-09-30
I had the same error with mplayer:

Linux RTC init error in ioctl (rtc_irqp_set 1024): Invalid argument
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

I notice that typing *echo 1024 > /proc/sys/dev/rtc/max-user-freq* while root solve the problem (well, of course!). But there is more.

The "system startup scripts", from what I understand, are in fact the .bashrc file (~/.bashrc).
*****
By adding the line *echo 1024 > /proc/sys/dev/rtc/max-user-freq* to the .bashrc it does solve the problem PERMANENTLY. For that, use your favorite editor (vi rules!).
To "reload" the .bashrc, just type *source ~/.bashrc*.
******
Now you can verify by typing *cat /proc/sys/dev/rtc/max-user-freq* : the value is now 1024.

Next time you'll boot the computer everything will be fine!

---

### Post by antidrugue on 2005-10-01
Sorry, my previous answer is just not true. It won't work has it is, because .bashrc doesn't set his preferences as of root.

---

### Post by rubyat on 2006-07-13
To set the rtc max-freq. at boot: boot in recovery mode which gives you root status.
do:    echo "dev.rtc.max-user-freq=1024" >> /etc/sysctl.conf

reboot and check /proc/sys/dev/rtc/max-user-freq

it should be 1024.

---

