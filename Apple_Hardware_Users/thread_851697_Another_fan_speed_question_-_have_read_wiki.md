---
title: "Another fan speed question - have read wiki"
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by rickcr on 2008-07-06
I'm really in a bind here. I like ubuntu and I want to run it instead of osx on this macbook pro (2nd or 1st gen.) The problem is the fans are running at 5535 rpm when the computer is completely idle with no apps running other than the basic gnome stuff. (Top shows the cpu at 1%.)

I really don't want my fans running this fast all the time. I've figured I'd look into how I can set things manually so following the wiki entry [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro") it says:

sudo modprobe applesmc
echo applesmc | sudo tee -a /etc/modules

Copy the files to your home dir: fan_speed1 , fan_speed2 , fan_speed3

Where are these files supposed to be? I figured the second command above should generate them? But I don't see them anywhere. All the second command returns is the echo output of "applesmc" 

Do others have their mbp fans running this fast when idle as well? Granted I'd rather them run fast than not fast enough, but this seems way too high.

---

### Post by kosumi68 on 2008-07-07
The files you are looking for must be downloaded (from the place pointed to by the poster); the command you executed only adds the applesmc module to your startup sequence.

The temperature of the macbooks (also Pro and Air) seems to be a general problem. There are many factors affecting the fan speed, of which the ambient temperature might be the most important one. If you are in a hot place, there might not exist any good solution.

---

### Post by cyberdork33 on 2008-07-08
Also see this wiki page:
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

---

### Post by Bucky Ball on 2008-07-09
May be check out this page;

[http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html](http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html)

If the fan is working overtime it could be the hard drive heating up the interior. Download 'smartmoncontrols' as directed and have a look at your 'load_cycle_count' and the hard drive temperature. If the load count is ticking over rapidly or the temperature is up (over about 50c say), you have a problem and that would probably explain the fan. You need to do this fix or something similar. After loading smartmontools, if you type ;

> sudo smartctl -a /dev/sda

in a terminal, you can find out all sorts about your machine.

The following page has a neat chart to calculate your hard drive's life expectancy and from that, you can figure out if your cycle count is something to worry about;

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

and a quote from later in that post;

> my machine had a load cycle of about 1 / minute before the fix, and zero now (I put hdparm -B 245). The temperature has gone up from 37°C to 41°C. It's a first generation apple macbook with a Toshiba MK603 hard drive. I had already found this kind of fix in a thread specifically about macbooks, but there they forgot to put the script in /etc/acpi/ac.d (only in battery.d). I'll see if I can find that thread and point those poor macbook owners to your thread.

The fix worked for me straight up, the count just about stopped and seems to be working fine. I could be off the money, but ya never know. Could be some fan controller or setting but I'd be more worried it is the hard drive causing the problem, as this is a known issue ... It does not apply to desktops unless they are using agressive power management.

Good luck

---

