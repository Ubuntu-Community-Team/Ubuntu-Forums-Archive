---
title: "Timestamp too far in future?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2007-08-09
Whenever I try to install something... i get 

```
sudo: timestamp too far in the future: Aug 10 00:30:20 2007

```

What does this mean and how do i fix it.

---

### Post by splintercellguy on 2007-08-09
I do not know, but perhaps your locale settings are out of whack?

---

### Post by Darkriser on 2007-08-09
Check your date and time settings and set real date/time. This will solve your problem.

Marcel

---

### Post by splintercellguy on 2007-08-09
Ah, and make sure your comp is syncing with an NTP server.

---

### Post by alienexplorers on 2007-08-09
Try synchronizing your clock with one of the time servers.

---

### Post by MenZa on 2007-08-09
> **alienexplorers said:**
> Try synchronizing your clock with one of the time servers.

In case you don't know, you can do this by running *sudo ntpdate ntp.ubuntu.com* (for the Ubuntu NTP server). If it complains that ntpdate is not installed, simply run *sudo apt-get install ntpdate*.

---

### Post by lavinog on 2007-08-12
> **MenZa said:**
> In case you don't know, you can do this by running *sudo ntpdate ntp.ubuntu.com* (for the Ubuntu NTP server). If it complains that ntpdate is not installed, simply run *sudo apt-get install ntpdate*.

I am having the same problem.
It wont let me use sudo because it complains about the timestamp being too far in the future
second correcting the date doesn't fix the problem...it is what caused the problem for me
my cmos battery died, the clock reset, I used sudo then set the time to the correct time
now i can't sudo anymore

Don't ask me why, but for me it is saying sudo: timestamp too far in the future: Mar 30 17:30:58 2008
I can't wait that long
I can probably dig and maybe edit a file manually, but i'm not sure how I am going to get permission to edit it without using a recovery disk (this is a remote server)
I can't even reboot it because I need sudo.

I think Alice Cooper wrote a song on this issue

---

### Post by Bachstelze on 2007-08-12
> **lavinog said:**
> It wont let me use sudo because it complains about the timestamp being too far in the future

Ow, I was wondering who stole my DeLorean :D

*sudo -K* will kill the stored timestamp, allowing you to use sudo again.

---

### Post by lavinog on 2007-08-12
> sudo -K will kill the stored timestamp, allowing you to use sudo again.

I think that did it
I say I think because it gave me the same error
and by accident i was going to try again but used lowercase k instead
so if -K didn't fix it, -k did

Thank you for your timely response
I hope it works for the OP

---

### Post by aysiu on 2007-08-12
A reboot usually helps, and you can do this from the GUI without root privileges.

---

### Post by lavinog on 2007-08-12
> **aysiu said:**
> A reboot usually helps, and you can do this from the GUI without root privileges.

ahh but it was a server with no gui

---

### Post by dr.faustus on 2007-09-06
I also had this problem on "Australia/Sydney" timezone. 

Then I ran this fix posted by ghotra;
[http://ubuntuforums.org/showpost.php?p=1330985&postcount=16](http://ubuntuforums.org/showpost.php?p=1330985&postcount=16)

All fine since...:)

---

### Post by Cato2 on 2007-09-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/43233](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/43233) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just had this problem on an old laptop where the CMOS clock is not too healthy.  Using Xubuntu 7.04 Feisty but this bug has been around for quite a while.

This happened because the CMOS clock (type 'hwclock' to view this, no sudo needed) was 2 hours ahead of the system clock.  No idea why this should matter to sudo...  

Anyway, here is one way to resolve this, from reading around:

1. Hit Alt-F1 (the GUI disappears but it's still running, don't worry!), then login as yourself, then check output of 'date' is OK, and compare to 'hwclock' - if they don't match, carry on with step 2

2. Type 'sudo -K' - kills any timestamp held by sudo for your user - may not be necessary as the timestamp is 'per terminal' (i.e. Alt-F1 is different terminal to a graphical terminal within Ubuntu GUI)

3. Type 'sudo hwclock -w' - this writes the system date/time into the CMOS clock

4. You're done, hit Alt-F7 to get back into your GUI.

Alternative **really quick workaround**:

1. Create a new terminal window or tab (this means a new tty device under /dev)

2. sudo as normal

I found that even after steps 1 to 4, I still couldn't sudo in the terminal I was using (under Xubuntu GUI) - not sure why.

This is really quite a pain, there should be at least a more helpful error message from sudo, suggesting you try a different terminal.  There's some discussion of this here: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/43233](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/43233) 

Ubuntu should have a better way of resolving this, or (better) ensure that sudo only uses the system date not hardware/CMOS clock, as that would have prevented this.

On the plus side, Feisty just recognised my Cisco WiFi card, which is nice!

---

### Post by lavinog on 2007-09-24
I found out why my timestamp was getting messed up.
turned out that the hard drive that was installed was somehow setting the date in cmos to 00/01/1983
I thought it was a cmos battery issue, but changing the battery didn't fix it...instead changing out the hd did fix it.
The date was getting messed up at POST prior to grub and linux loading.

The work around for the sudo -K problem was to use another ssh terminal
sudo su
ls /var/run/sudo/username
> -rw------- 1 root root 0 2008-04-20 12:05 0
-rw------- 1 root root 0 2007-09-24 13:51 1

notice the date on file 0.
touch /var/run/sudo/username/0
exit

then everything worked

---

