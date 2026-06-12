---
title: "cannot resize partition... help please"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by LamB on 2006-01-06
hi, i cannot resize the partition on my dell notebook. im trying to partition it with the ubuntu live cd (gparted). any suggestions??

---

### Post by stuporglue on 2006-01-06
I had the same problem today. 

Gparted would show it being resized, but pending, then I'd hit apply, and it would go back to it's orriginal state. 

I installed qtparted (in the live CD session) and it worked fine, first try. :-) You'll need to enable some more repositories to get qtparted though. Here's one option -- grab my sources.list, update then install qtparted

On the live CD, open a terminal and....

$ sudo su
# cd /etc/apt
# wget stuporglue.org/downloads/sources.list
# mv sources.list.1 sources.list
# apt-get update
# apt-get install qtparted
# qtparted

Good luck!

---

