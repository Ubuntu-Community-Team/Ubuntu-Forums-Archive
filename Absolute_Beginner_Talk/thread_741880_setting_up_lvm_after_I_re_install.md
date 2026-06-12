---
title: "setting up lvm after I re install"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by reeseslover531 on 2008-04-01
Hello.  So I am about to reinstall ubuntu, and I have two backup drives that are lvmed together to look like one.  My problem is I don't want to lose that data or anything.  When I reinstall, how to I initialize the lvm so that it realized that they were already lvmed and just re-sets everything back up?

Thanks

---

### Post by justleen on 2008-04-01
you wil lhave to define the lvm during install, and make very sure you dont tick "format"

you could run the install without touching those drives, then later add lvm support, and redefine the volume groups. I think i'd go for the latter.

---

### Post by reeseslover531 on 2008-04-01
YA that is what I will probably do.  These aren't boot drives so there is no need to do it during install.  So pretty much just go through the same procedure I used to set them up in the first place, anything I should be careful of?

---

