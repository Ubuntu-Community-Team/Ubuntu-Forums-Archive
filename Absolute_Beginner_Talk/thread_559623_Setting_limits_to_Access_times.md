---
title: "Setting limits to Access times"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by tankster on 2007-09-25
I apologize if this has been posted. I did a search and could not find anything on this topic.

I would like to limit access times for my son. I would like to set his account up so he gets 2 hours computer access a day and only 1 of those hours for internet access. I believe this should be possible. Your help and guidance is appreciated. Thank You.

Sincerely,

Ken

---

### Post by ddrichardson on 2007-09-25
This was a proposal for [Breezy]("http://ubuntuforums.org/showthread.php?t=42465"), but was considered a low priority, unless those proposing could do the work.

Personally I think it's a good idea and have ideas as to how to implement it, possibly involving timeoutd.

There are "dirty" solutions using cron and bash scripts but I don't like the potential for corrupting data. Solaris can do this by using new account generation per login but I think this wont fit the bill here.

---

