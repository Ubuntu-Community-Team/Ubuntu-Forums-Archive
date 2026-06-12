---
title: "best version for my pc"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-02-22
which version (ubuntu, xubuntu etc.) would you recommend for me to use. i have a 1.4GHz processor and 384 Mb RAM. and i only use for music, internet and basic audio recording. 

thanks

---

### Post by fusiachi on 2007-02-22
Ubuntu 6.06 or 6.10 should run alright.

Xubuntu might run a bit snappier, given your RAM.

---

### Post by netkid91 on 2007-02-22
Ubuntu is very light on system spec's man.  My sisters 600MhZ Celeron (AKA Celery) machine with 180-something MB of RAM runs it (albeit a little slow), you machine has just a little less RAM than mine, it'll run just fine (recommended RAM is 256MB).
So just go with vanilla Ubuntu.

---

### Post by jml on 2007-02-22
I agree, Ubuntu should run reasonably well with the system you have.  One option would be to download both Ubuntu and Xubuntu and try them both out.  Xubuntu will run a bit faster, but you may prefer the added functionality the Gnome destop environment offers.  Also, most of the educational material will focus on Ubuntu.  So looking information up for new users may be easier with an Ubuntu install.

Joe

---

### Post by darkeale on 2007-02-22
yeah thanks guys. tried all 3 and im sticking with ubuntu. can anyone tell me how to reset the login screen back to the ubuntu one cause mines become the xubuntu one?

---

### Post by punx45 on 2007-02-22
when you go to the sessions chooser, there should be a button or check box that says "make selection default." check that and pick gnome, which is the default ubuntu.

i think that should do the trick.

though i haven't used any *buntu GUIs in a while...   aqua is what i point and click with now

---

### Post by netkid91 on 2007-02-22
sudo dpkg-reconfigure gdm
Select GDM from the list and you'll be set.

---

### Post by pissedoffdude on 2007-02-22
> **darkeale said:**
> yeah thanks guys. tried all 3 and im sticking with ubuntu. can anyone tell me how to reset the login screen back to the ubuntu one cause mines become the xubuntu one?

Since your probably getting a kubuntu or xubuntu splash screen you can remove it by doing this:```
sudo update-alternatives --config usplash-artwork.so
``` and select the appropriate usplash (probably the first one)
then this ```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by darkeale on 2007-02-22
yeah i got it now. thanks a lot for the help everybody

---

### Post by netkid91 on 2007-02-22
That's what we are here for :)
Have a good day and happy desktop-ing.

---

