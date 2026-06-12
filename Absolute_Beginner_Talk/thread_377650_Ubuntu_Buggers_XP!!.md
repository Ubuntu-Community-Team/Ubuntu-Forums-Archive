---
title: "Ubuntu Buggers XP!?!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by BigBabyDaddy1968 on 2007-03-06
I burned the Ubuntu live cd, ran checksums, and made sure the disk checked out ok.  The only oddity I found was I couldn't run Firefox from the live cd, but I thought that was just a hiccup...so I took the plunge and installed, following psychocats' instructions.  I get to the final screen, which tells me to either continue running from the live cd, or take it out and reboot (I chose the latter)...but upon reboot, I get the ol' BSOD, telling me windows had to shut down to protect my computer.  The live cd would still boot (alas, no firefox love), but it won't re-install.  I also couldn't get to XP no matter what I tried---

The problem turned out to be the automatic partitioning shrank the partition for XP too much and corrupted it.  I was finally able to reinstall the XP OS late last night thanks to the help of a good buddy half way across the country (gotta love IM) and repartition the HD.  I've also made the partition scheme very simple, since I want to dual boot: half allocated to XP and half for Ubuntu.

However, before I try to reinstall Ubuntu (this hasn't remotely shaken my n00bish confidence...I learned a lot and am more determined than ever, especially as it seems my problems were purely user-error), **does it sound like the iso might be corrupted or otherwise [B]bad**, since  I can run everything *but *FF from the live cd?[/B]  [Bold added so readers can get to my Q without wading through the rest....]

My machine is a new (this past Xmas) Dell XPS 410 Media Center Edition running XP SP2 with a single 250GB HD and 2GB RAM.

So...have a laugh, lend a hand, or offer sympathy.  Any insight would be greatly appreciated.  (BTW, the buddy who helped me is a member here: Sweet Spot.  Much thanks.)

BBD

---

### Post by kanha on 2007-03-06
if once you have installed with that cd then it is sure that cd is right.
may be you should try partitioning by manually (not autopartition) during install
and what you mean by saying that now it is not reinstalling,what is the error given by cd.

and finally don't panic.post details here, we will find solutions :)

---

### Post by BigBabyDaddy1968 on 2007-03-06
> **kanha said:**
> if once you have installed with that cd then it is sure that cd is right.
may be you should try partitioning by manually (not autopartition) during install
and what you mean by saying that now it is not reinstalling,what is the error given by cd.
Thanks for the reply.  The cd doesn't give an "error" per se, it just won't let me get past the partitioning screen.
> and finally don't panic.post details here, we will find solutions :)
I just saw I double-posted the thread somehow.  Sorry about that...it's not like I don't generally know how to behave on a forum such as this.

Thanks again.

---

### Post by tubasoldier on 2007-03-06
You may have gotten some garbled data for the iso. but that is highly doubtable since you said the checksum turned out ok.

Above everything else, backup your data! defrag the crap out of your windows partition to compress the data in windows as much as possible. And then like Kanha said, it would probably be best for you to do the partitioning manually instead of the automatic one.

---

