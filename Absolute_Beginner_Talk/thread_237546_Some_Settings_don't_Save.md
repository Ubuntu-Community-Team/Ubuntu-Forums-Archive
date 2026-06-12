---
title: "Some Settings don't Save"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by splot on 2006-08-16
Okay, I just got back into Ubuntu after a slight sojourne.
According to the "About" page, I'm running Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006. I know I updated a bunch of stuff yesterday, altho some packages weren't available.

Some settings don't save when I reboot!  My DNS, for example, must be reset every time I reboot.  Also, it doesn't want to save my disc setup, I reboot and nothing's mounted in the right place or mounted at all in some cases.

Does anyone know why this is, and/or how I can fix it??  It's rather frustrating, I dual-boot for a reason and extra messing around every time I reboot is a hassle. :(

---

### Post by kebes on 2006-08-16
Okay this is an odd problem. I don't have a solution for you, but here are some things to try:

Take a look at your "/etc/fstab" file, which lists device mounting:
```

more /etc/fstab

```

Then modify your devices the way you want. (I assume you are doing this in the system settings control panel or something?) Then take a look at "/etc/fstab" again. Did it change? If it did change, reboot the computer and look at it again. Did it change ~back~?

You can post the contents of your fstab here to help with the troubleshooting.


For DNS, follow a similar procedure. I believe DNS settings are stored in "/etc/resolv.conf", but also take a look at:
/etc/resolv.conf
/etc/hosts
/etc/hostname
/etc/network/interfaces

See if these files are updated after you make changes to your network settings. Hopefully this will give us a hint as to what is going wrong. (File permissions? Startup script overwriting settings?)

Hope that helps!

---

### Post by splot on 2006-08-16
Well, harddisk problem is solved, apparently if I edit it directly in nano, it works fine, it's just the gui tool that had some issue.

But the DNS...well, it reverts on bootup.  It *does* change it in /etc/resolv.conf when I change it thru the gui tool, but it doesn't stick.
Could it concievably be an issue with my local DNS servers...?

---

### Post by sailor2001 on 2006-08-16
did you ctrl-x (save) after terminal typing?

---

### Post by splot on 2006-08-16
A) Of course.
B) the initial problem was through the gui tool, and no i never hit the "Cancel" button.

---

### Post by kebes on 2006-08-17
> **splot said:**
> Well, harddisk problem is solved, apparently if I edit it directly in nano, it works fine, it's just the gui tool that had some issue.

At least some of it is fixed...

> But the DNS...well, it reverts on bootup.  It *does* change it in /etc/resolv.conf when I change it thru the gui tool, but it doesn't stick.
Could it concievably be an issue with my local DNS servers...?

In your network settings, if you have it set to "automatic IP" (i.e.: DHCP) then it obtains the DNS settings over the network. Are other computers on the same network having problems? Is there any way you can set your network to offer static IPs instead of using DHCP?

---

### Post by splot on 2006-08-24
That's it, that's the problem.

So yeah, it's set to DHCP, because I don't know what IP I should use and I didn't realize that'd keep resetting the DNS servers.

I'll get with my roommate when he returns and see what IP I should use, and fix it.  thanks!! :KS

---

### Post by CoolioVendetta on 2006-08-24
[http://ubuntuforums.org/showthread.php?t=545](http://ubuntuforums.org/showthread.php?t=545)

Try that one bud, worked for me (4th post down the bit about /etc/dhcp3/dhclient-script).

Chances are the code you need to change wont be exactly the same as what's been written there.  The first block of code in the file is the bit that needs changing though.

---

