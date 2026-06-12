---
title: "ASUS Eee PC 1225B"
date: 2012-04-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by 00b00nt00 on 2012-04-30
Specs: [http://www.asus.com/Eee/Eee_PC/Eee_PC_1225B/#specifications](http://www.asus.com/Eee/Eee_PC/Eee_PC_1225B/#specifications)

Whenever I attempt to shut the computer down via the shutdown menu, the computer simply reboots.

Is there any way of fixing this? I'm using Ubuntu 12.04.

---

### Post by c_hai on 2012-04-30
you open terminal

$ sudo shutdown -h now

---

### Post by 00b00nt00 on 2012-04-30
I tried "sudo shutdown -h now".

No change - the computer reboots.

---

### Post by D@NO on 2012-05-01
Hi everyone! Same problem here!
I've ASUS 1225B with APU E-450 and I'm unable to shutdown, suspend or hibernate the computer!
I've tried also a Fedora based distro (Fuduntu) but I experienced the same problems.

---

### Post by 00b00nt00 on 2012-05-02
EDIT: PROBLEM IS NOT SOLVED.

I'll go back to Win 7 and try Ubuntu again when 12.10 comes out.

---

### Post by D@NO on 2012-05-09
I just discovered that when the netbook is battery powered it can be shut down properly. The problem persist if it is AC powered.
(I installed jupiter and its eee-support, I don't know if this can be related.)

---

### Post by c_hai on 2012-05-12
You can use it normally.

---

### Post by 00b00nt00 on 2012-05-16
> **D@NO said:**
> I just discovered that when the netbook is battery powered it can be shut down properly. The problem persist if it is AC powered.

I can confirm this quirk.

---

### Post by 4thelove on 2012-05-26
Hello,
I am having the same problem with the shutdown option. And, yes, you can shutdown only when the computer is on battery power. Has anyone been able to find a fix?
Also, my computer freezes occasionally in lightdm. Anyone else having this problem?

---

### Post by xapantu on 2012-05-28
See this bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951143) The solutions, at the end, work here.

---

### Post by 4thelove on 2012-05-29
I can confirm the the following fixes work:

1) Suspend problem
     Fix: 

[http://askubuntu.com/questions/53372/suspend-hibernate-doesnt-work-on-an-asus-laptop](http://askubuntu.com/questions/53372/suspend-hibernate-doesnt-work-on-an-asus-laptop)

2) Computer restarts instead of shutting down
     Fix:  

"If you also have the problem that the computer doesn't shut down, but  always reboots if you hit the shutdown button, put this command in your  /etc/rc.local"

          echo "LID" > /proc/acpi/wakeup (right before the "exit 0")

*for this fix you will have to be logged in as root. Here is a link the show you how to log in as root:  

[http://askubuntu.com/questions/141741/re-enable-graphical-root-login-on-12-04-lts](http://askubuntu.com/questions/141741/re-enable-graphical-root-login-on-12-04-lts)

The only other problem I still cannot find a fix for is the freeze problem. Basically every 3 or 4 times I turn on my computer it will boot up fine all the way to the login in lightdm. I've tried using the automatic login and it will freeze once Ubuntu is fully loaded. At this point the touchpad and keyboard does not work. Would really like some help with this as I have to manually hold the power down button until my computer shutdown, which isn't good for the hard drive.

---

### Post by iris-n on 2012-06-25
The solutions from the bug report were not enough for me. I had also to disable fgrlx and use the radeon driver instead.

I also got the problem of no-input once in a while, no luck with it yet, though.

---

### Post by iris-n on 2012-07-02
There is a workaround to the freeze problems, as reported by &#321;ukasz in the bug report [https://bugs.launchpad.net/ubuntu/+bug/1014240](https://bugs.launchpad.net/ubuntu/+bug/1014240)

You only need to add options i8042.reset and i8042.nomux to your boot parameters; it is working for me so far.

---

### Post by 00b00nt00 on 2012-10-02
Ouantal seems to fix the shut-down problem, and the open source driver is better optimised, too.

Looking good so far.

---

