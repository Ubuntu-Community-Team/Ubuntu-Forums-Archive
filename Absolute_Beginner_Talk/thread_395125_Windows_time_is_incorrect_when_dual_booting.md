---
title: "Windows time is incorrect when dual booting"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by linuxmonkey on 2007-03-27
Whenever I boot back into windows from Ubuntu, my windows time jumps ahead about 6 hours.

Any ideas why this is happening?

I did a search, didn't find much info on this.

---

### Post by nike984 on 2007-03-27
when your in Ubuntu partition, check the clock preference.
I think you would have activated the "use UTC" option.
Inactivate that option and it will probably solve your problem.

---

### Post by n8bounds on 2007-03-27
you told ubuntu that your bios clock was set to UTC time, which windows never assumes for some reason; try searching on how to toggle the bios UTC switch

---

### Post by linuxmonkey on 2007-03-27
I didn't see this option on install.  When I right-click the clock and choose preferences, UTC is unchecked.  I then found someone else that had the same issue, and they used the command below:

sudo gedit /etc/default/rcS

There is a setting for UTC in that file (YES/NO)

Mine was set to Yes.  After changing it, I don't have any issue with the time in Windows.

Thanks for the replies.

---

