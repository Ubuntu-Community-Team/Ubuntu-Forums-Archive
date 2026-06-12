---
title: "Dual booting MythTv and Gutsy?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-17
Can I dual boot Mythbuntu with my regular Gutsy desktop still operational? I'm just not really sure on how the whole Mythbuntu application works. 

I am already dual booting Xp and Gutsy. 

Basically will I still have my Gutsy desktop and apps if I install Mythbuntu?

---

### Post by emarkd on 2008-02-17
MythBuntu is build on Xubuntu, so you'd really be dual-booting Ubuntu and Xubuntu.  You can do that if you want, no problem.  Another option is to just install Mythtv in Ubuntu.  Then you wouldn't even have to reboot.

---

### Post by JoshuaRL on 2008-02-17
Well, that depends on how you install it.  Mythbuntu is a full Ubuntu implementation with a MythTV version of XFCE as the X session.  This will install a full OS on your harddrive, partitioned or not depending on your choice.

If you go into Add/Remove there are also MythTV frontend (GUI) and backend (server) packages available.  If you wanted to keep your desktop, apps, and settings then this would be the way to go, just open the frontend when you want to use MythTV.

---

### Post by wolfen69 on 2008-02-17
> Can I dual boot Mythbuntu with my regular Gutsy desktop still operational?

that's exactly what i'm doing at the moment. i wanted to have my media center OS (mythbuntu) on a seperate hard drive. ive never installed mythtv on top of ubuntu, so i can't comment on that.

---

### Post by ssharps711 on 2008-02-18
> **JoshuaRL said:**
> Well, that depends on how you install it.  Mythbuntu is a full Ubuntu implementation with a MythTV version of XFCE as the X session.  This will install a full OS on your harddrive, partitioned or not depending on your choice.

If you go into Add/Remove there are also MythTV frontend (GUI) and backend (server) packages available.  If you wanted to keep your desktop, apps, and settings then this would be the way to go, just open the frontend when you want to use MythTV.

Is there a guide available for this?

---

### Post by JoshuaRL on 2008-02-18
Which one?  If you want to dual boot Mythbuntu, then it should be the same as dual-booting the normal system.

Using the Add/Remove app should be pretty straightforward too.

But I have a better solution for you.

```

sudo aptitude install mythbuntu-desktop

```

That will install the Mythbuntu Desktop Environment, which you will be able to access from the login window under sessions.

I just did it, worked great.

---

