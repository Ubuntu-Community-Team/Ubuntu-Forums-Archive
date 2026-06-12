---
title: "new updates"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-21
hi,

I had to re-install gutsy on my hd. At the first time I installed gutsy there were a couple of new updates symbolized by a orange box with a white sort of sun inside it on the top right hand corner of he screen. But after I re-installed it (i re-installed it just now) there were no orange box on the top right of the screen. That orange update box showed up when I installed fiesty and gutsy for the first time. but after i deleted the first gutsy and re-installed it no orange update box showed up.

What do u think the problem is?

Thnx  :popcorn:

---

### Post by idodos on 2007-10-21
Well u see, when u install Ubuntu it actually downloads updates in the installation process.
So u don't have any problem :)

---

### Post by FuturePilot on 2007-10-21
Make sure you have all the repos enabled. System>Administration>Software Sources

---

### Post by limac on 2007-10-21
hey,

But then why isn't my symantis package manager still lacking of some of the things i saw there before after updating from the orange box with a white star like thing in it on the top right side corner of the screen.

---

### Post by limac on 2007-10-21
thanks futurepilot that really helped

---

### Post by jd65pl on 2007-10-21
Check your repositories as stated above then check if you require any updates

```
sudo aptitude update
```

Then upgrade any packages that need upgrading.

```
sudo aptitude upgrade
```

I'm not sure what the problem is you are having.

---

### Post by por100pre1 on 2007-10-21
> **jd65pl said:**
> ```
sudo aptitude upgrade
```

The aptitude upgrade command is being deprecated in Gutsy. The new command is:

```
sudo aptitude safe-upgrade
```

Just to let you know that. :)

---

