---
title: "[SOLVED] switch from ubuntu to kubuntu"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-01-16
Hi,
I installed Ubuntu Gutsy several months ago and have found that most of the apps that I like are K.  So I'm considering the switch to Kubuntu.

However, I'm not certain of the best way.  I have read many posts that seem to indicate that I can simply install Kubuntu from the cd and it won't wipe my hard drive.  That doesn't seem possible.  It also seems like I will then have 2 os's in a single partition, which doesn't seem smart.

Advice/suggestions most appreciated.

Thanks

---

### Post by p_quarles on 2008-01-16
```
sudo apt-get install kubuntu-desktop
```
This will certainly not remove anything from the drive, and will give you the new option of choosing between Gnome and KDE at the login screen.

---

### Post by Sef on 2008-01-16
Read [Psychoat's Install KDE]("http://www.psychocats.net/ubuntu/kde").

---

### Post by julian67 on 2008-01-16
easy way:

```
sudo apt-get install kubuntu-desktop
```

KDE and Gnome and Xfce etc are not different Operating Systems, they are simply different Desktop Environments. The underlying OS is the same whichever you use. You can have multiple Desktop Environments on the same OS. You choose which to use at log in time (option under session) but all the applications are available to you whichever you choose. If you decide you prefer a KDE only environment and want to remove all the Gnome stuff then have a look at this article [http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by thelatinist on 2008-01-16
Try out the Kubuntu LiveCD to see if you like it.  If you decide to go with it, I strongly suggest a fresh install.  While it is perfectly possible to install the kubuntu-desktop package, you are going to find that your menus are cluttered with Gnome apps you don't want.  Better to start from scratch, I think.

---

### Post by brett611 on 2008-01-17
Thanks all.  I had read psycho cats instrux but wasn't sure about the impact.  I was under the impression that the various flavors of ubuntu (k/x/etc) worked like XP Home/XP Prof

I'll try it out and if I end up liking it I think I'll do a fresh install after backup as I agree with the post re: clutter

---

