---
title: "Upgrading Pidgin"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-10-13
I am having a strange problem.

I installed pidgin 2.1.1 a while back. I can't remember whether it was from a .deb or I compiled it from source.

In any case I decided that I would update it to 2.2.1. So I downloaded the source and I did the ./configure, make, make install.

When I started pidgin (by going to applications>internet>pidgin) and checked the about it said 2.1.1. So I tried sudo apt-get remove pidgin, and the compiled the 2.2.1 again. Still the same thing.

So then I went to getdeb.com and downloaded the pidgin and pidgin-data packages for 2.2.0 (at least its newer than 2.1.1). I installed them fairly easily (as it usually is with deb packages).

When I started up Pidgin and checked the about I still got 2.1.1. 

So basically I don't mind completely erasing Pidgin and starting again, but I have a lot of settings (guifications, etc) that I don't really want to redo. Is there any easy-ish way to upgrade?

---

### Post by funrider on 2007-10-13
i think 7.10 will come with pidgin. not 100% sure. if this is true, you can upgrade it from the repository.

---

### Post by ghost_ryder35 on 2007-10-13
check the repos to see if they added the updated file?  If not you will have to make a link of the new install to the menu and remove the old version of pidgin by hand.  you probally compiled it yourself thats why it didnt upgrade the files.

---

### Post by ghost_ryder35 on 2007-10-13
> **funrider said:**
> i think 7.10 will come with pidgin. not 100% sure. if this is true, you can upgrade it from the repository.

7.10 come's with Pidgin

---

### Post by abhiroopb on 2007-10-14
As it stands not really interested about 7.10. I just want to upgrade my current pidgin. If I did install it from source how do I uninstall?

---

### Post by FredB on 2007-10-14
If you installed it from source, just get the source.

1) ./configure
2) sudo make uninstall

It could help ;)

---

