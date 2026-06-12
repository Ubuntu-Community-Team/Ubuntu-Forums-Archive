---
title: "Disable cron daemon. Safe?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by benton on 2007-11-03
Hi there, I run Ubuntu 7.10 on a laptop and wonder if I can safely disable the crond daemon. I don't schedule any task myself but I don't know if it is used by the system and should be left on.

Thanks for any help,

-Benton

---

### Post by 444 on 2007-11-03
I think you'll stop getting automatic updates that way, so if you're ok with that, go ahead. Don't know why you'd do that, though...

Oh, and it does log rotation as well, but that is not particularly important (it's supposed to keep the logs from filling up the whole disk but that'll take a while (probably years) to happen).

---

### Post by dcstar on 2007-11-03
> **benton said:**
> Hi there, I run Ubuntu 7.10 on a laptop and wonder if I can safely disable the crond daemon. I don't schedule any task myself but I don't know if it is used by the system and should be left on.

Thanks for any help,

-Benton

It is generally pointless mucking around with any of the system components in a Linux/Unix system, there is usually little (or any) benefit and a high potential of problems.

It's like removing some of the internal organs of your pet because you don't understand what they are for.

---

