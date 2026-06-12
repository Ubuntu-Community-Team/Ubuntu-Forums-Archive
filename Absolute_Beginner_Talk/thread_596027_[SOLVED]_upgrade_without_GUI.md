---
title: "[SOLVED] upgrade without GUI"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by bdk6m2007 on 2007-10-29
What's the procedure to upgrade (in this case from Fiesty to Gutsy, but I think it's really a general question) *without* a GUI?

When I run [FONT=Courier New]update-manager -c[/FONT] just to be sure it can see the servers, etc. I get boatloads of GTK assertion failures and ultimately a segmentation fault.

Can I just edit /etc/apt/sources.list and change all [FONT=Courier New]fiesty[/FONT]'s to [FONT=Courier New]gutsy[/FONT]'s??

---

### Post by bdk6m2007 on 2007-10-29
I had googled before, but not enough.  :)

The solution is [do-release-upgrade]("https://help.ubuntu.com/community/GutsyUpgrades#head-f2435a45758bb5836f8e5b87e90045463f8c6ec7").

---

