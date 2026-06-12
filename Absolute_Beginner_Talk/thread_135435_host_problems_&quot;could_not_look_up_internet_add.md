---
title: "host problems: &quot;could not look up internet address&quot;"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by hwliang on 2006-02-23
So, when I log into Ubuntu, I get this message:

"Could not look up internet address for boggy. This could prevent GNOME from operating correctly. It may be possible to correct the problem by adding boggy to the file /etc/hosts."

"boggy," by the way, is the name of my computer.

Usually, I just ignore the problem and log in. But I've found that now I can no longer sudo in the terminal. When I try to sudo, I get this message:

> sudo: unable to lookup boggy via gethostbyname()

any ideas?  My /etc/hosts file looks like this:

> # The following lines are desirable for IPv6 capable hosts


and my etc/hostname looks like this:

> boggy

I'm a bit afraid that without sudo access, I won't be able to fix the problem even if I knew where it is...

Lastly, I believe this problem arose from me messing with my wireless settings under the "Networking" app. I can no longer run it, which is probably due to me not being able to sudo.

Any help would be appreciated!

---

### Post by pestilence4hr on 2006-02-23
This has got to be one of the more frequently asked questions...do a search on the forums, you'll easily find the answer.  Basically you need to boot into rescue mode or from a live cd and edit /etc/hosts.

I'll even give you a big clue:

127.0.0.1   localhost.localdomain   localhost   boggy

should be in your /etc/hosts

---

### Post by hwliang on 2006-02-23
pestilence4hr, thanks for the tip. apologies for not doing a forum search first (i didn't know what to search for, honestly, and was getting frustrated after a few weeks of this). i'll give your hint a shot (boot into recovery mode, nano etc/hosts, insert the above, rinse and repeat), and report back with results.

//edit: yep, it worked. thanks for the help!

---

