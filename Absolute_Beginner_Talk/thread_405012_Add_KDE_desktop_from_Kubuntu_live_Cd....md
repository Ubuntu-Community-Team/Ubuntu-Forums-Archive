---
title: "Add KDE desktop from Kubuntu live Cd...?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2007-04-09
im currently using ubuntu (GNOME) at home... can i switch to KDE desktop using Kubuntu live cd without installing it? :)

---

### Post by overdrank on 2007-04-09
> **Nhatz said:**
> im currently using ubuntu (GNOME) at home... can i switch to KDE desktop using Kubuntu live cd without installing it? :)

Hi and welcome, I believe you will be able to install KDE from the cd but you can also install it from  Synaptic manager. That may be your best bet. Good luck!:)

---

### Post by capitalistpiglet on 2007-04-09
to install the kde desktop just run the command 
```

sudo apt-get install kubuntu-desktop

```

---

### Post by zvacet on 2007-04-09
I never try it but since you have Kubuntu CD
```
sudo apt-cdrom add
``` 
```
sudo aptitude install kubuntu-desktop
```

Just a sugestion.

---

### Post by PointSource on 2007-04-09
No, it won't work because the liveCD does not have all those bits as *.debs. It uses a pre-built file system that it copies to your hard drive during the install process. You would have more luck with an alternate install CD but then again it might have a smaller base file system image too. A couple of *.debs would need to be downloaded off the net. Watch your bandwidth though!

---

