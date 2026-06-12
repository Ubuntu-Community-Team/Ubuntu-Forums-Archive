---
title: "How to install Gnome on 7.10"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-13
How do you install Gnome desktop on 7.10 server?

---

### Post by Hospadar on 2008-03-13
if you want a graphical login, the easiest way is by installing gdm I believe
```
sudo apt-get install gdm
```And then restart the machine or ```
sudo /etc/init.d/gdm start
```
You might need/want other packages too though, I think ubuntu-desktop is the general package that will install everything for you that you get on a normal installation.

---

### Post by jken146 on 2008-03-13
> **BlizzofOZ said:**
> How do you install Gnome desktop on 7.10 server?

If you want the full-blown Ubuntu GNOME desktop with all the usual pre-installed apps, then ```
sudo aptitude install ubuntu-desktop
```

---

### Post by Tatty on 2008-03-13
try

```
sudo apt-get install ubuntu-desktop
```

If youre using a server perhaps you might want something a bit more lightweight like xubuntu:

```
sudo apt-get install xubuntu-desktop
```

---

### Post by tad1073 on 2008-03-13
When is gnome 2.22 going to be in the repo's?

---

### Post by Tatty on 2008-03-13
> **tad1073 said:**
> When is gnome 2.22 going to be in the repo's?

It wont be,  the repos are frozen after each release, the only things that are changed are security updates...

The only exception is if you use the ubunt-backports repo, which is not officially maintained, but does offer the latest versions of some software.  Although I have no idea if they have gnome 2.2 in it.

Wait for Hardy Heron, that should feature the latest stable gnome.

---

### Post by BlizzofOZ on 2008-03-13
Yes, in my searching I've that command:
sudo aptitude install ubuntu-desktop

Sounds like you can install all or basic desktop with option to add more functions.

What is gdm then?

Does anybody have a link(s) to somewhere that might explain in detail?

---

### Post by Tatty on 2008-03-13
gdm is the graphical login screen for gnome.

---

### Post by BlizzofOZ on 2008-03-13
Yes, I'll be running a server... what is the concern over running the full blown desktop on the server?

Is it the disc space required or CPU usage?

---

### Post by BlizzofOZ on 2008-03-13
> **Tatty said:**
> gdm is the graphical login screen for gnome.

Is GDM included in the full gnome desktop?

---

### Post by jken146 on 2008-03-13
> **BlizzofOZ said:**
> Is GDM included in the full gnome desktop?

Yes.

---

### Post by Tatty on 2008-03-13
> **BlizzofOZ said:**
> Yes, I'll be running a server... what is the concern over running the full blown desktop on the server?

Is it the disc space required or CPU usage?

Well usually servers are seen as more pratical rather than aesthetic, so people usually prefer to use a lighter GUI since there is no point eating up the resources...

It depends on what you want.  If it is going to be in heavy usage then it might speed things up to run xubuntu.

---

