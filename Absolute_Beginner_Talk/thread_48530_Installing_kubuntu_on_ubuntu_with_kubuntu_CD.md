---
title: "Installing kubuntu on ubuntu with kubuntu CD"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-07-12
HELP ME!!!

I have Ubuntu installed on my system. And I have this Kubuntu install CD also.
Can I install Kubuntu ON Ubuntu with the Kubuntu CD? I mean can I have a KDE desktop in Ubuntu WITHOUT replacing Ubuntu or going ONLINE, with the help of the Kubuntu CD only? Can't I install KDE packages from Kubuntu install CD on my Ubuntu system?

Is this possible?
Hope u got my point.

Plz help the newbie.

Thanks

---

### Post by SGC on 2005-07-12
I never try it, but it should works. From the terminal do the following:

```

sudo apt-cdrom add

```
Insert kubuntu CD and press enter

Then update the repositories list to include kubuntu CD:
```

sudo apt-get update

```

Finally, install kubuntu-desktop:
```

sudo apt-get install kubuntu-desktop

```

---

