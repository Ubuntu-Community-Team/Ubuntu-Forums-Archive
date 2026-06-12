---
title: "Boot with GDM rather than KDM"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2007-02-24
I've been running Gnome since I first installed Ubuntu a while back. Wanting to try KDE I downloaded and installed it yesterday - and it's been bothering me since...

During the installation I (in my infinite wisdom) selected an option that made sure I have a Kubuntu boot screen instead of my regular Ubuntu screen.

What I now want is to completely remove Kubuntu from my machine, but after trying to follow various instructions found in this forum I'm short of quitting and posting this instead.

Can someone please advise me as to how I can regain my old boot screen and remove the KDE completely?

Sincerely
Robert Leithe

---

### Post by Kateikyoushi on 2007-02-24
I recently uninstalled KDE as well.
To change the login manager go to System > Administration > Login window, here select what you like.

To remove KDE.

```
sudo aptitude remove kubuntu-desktop
```

---

### Post by Robert Leithe on 2007-02-24
When I click System > Administration > Login window nothing happens. That is, I'm prompted for, and enter the root password, but after that nothing happens.

I tried to change the /etc/X11/default-display-manager from

/usr/bin/kdm

to

/usr/bin/gdm

But then no GUI would launch, so I had to change it back.

---

### Post by Royel on 2007-02-24
```
sudo dpkg-reconfigure gdm
```


Enjoy!

---

### Post by rusty4r on 2007-02-24
I did the same thing as you did and I prefer gnome as well, but the funny thing is I prefer the blue and white on the part where it is loading the kernel and you see the text scrolling by. I could never read the dark orange of ubuntu. So I'm happy with it being that way. My default session is Gnome so my login window and every thing else is still gnome.

---

### Post by Robert Leithe on 2007-02-24
My desktop environment and logon screen are now back to "normal". But the shutdown and startup screens are still Kubuntu.

---

