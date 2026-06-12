---
title: "Cannot start X server on Oneiric"
date: 2011-12-02
forum: Apple Hardware Users
---

### Post by neopium on 2011-12-02
Hi,

I have a MacBook Pro 3,1 (year 2007) and just installed Oneiric on it.

I had plenty of problems (it took me more than 12 hours to have it "work").

First, it was not possible to boot on the Live CD. So I downloaded the alternate mac edition. Then I had plenty of trouble setting up the partitions with LVM.

I finally gave up and partitioned it with traditional ext4 partitions, but rEFIt didn't want to start Ubuntu (no operating system) and its partition tool crashed. I had to install another command line tool on the Mac to change to partition tables...

And finally, I could start it... but... I have an awful graphical artifact displayed... and nothing else.

I thus turn to console mode, logged in and typed "X" to start the X server... It told me "command not found". I check my $PATH variable, which includes /usr/bin, / usr/sbin, /usr/local/bin, /usr/local/sbin, /bin and /usr/games

I then tried "sudo apt-get update" but it seems I have no network connection (my computer is plugged via ethernet).

ping [www.google.com](www.google.com) returns unknown host, and ifconfig confirms I am offline...

Wow

What should I try now?

Any advice is welcome :-)

---

