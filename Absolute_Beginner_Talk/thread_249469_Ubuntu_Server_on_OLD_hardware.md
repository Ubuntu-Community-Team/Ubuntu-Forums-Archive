---
title: "Ubuntu Server on OLD hardware"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Pocket Aces on 2006-09-02
Hey everyone,

I run Ubuntu on my laptop but have never used it for anything server oriented.  In the past I've run servers with RedHat and FreeBSD.  I acquired a system with a whopping 96 megs of memory and a 233 Mhz processor.  My old freebsd server had stats only slightly better.  The system is only going to be used for a local fileserver for my flatmates and I.  Ubuntu doesn't seem to want to load on the system.  (Shocking that a live cd can't load w/ 96 megs to work with, I know).

I really like ubuntu for the fantastic community and ease of use... but for this project would I be better off going back to a more bare-bones system like I can setup w/ freebsd?

---

### Post by benfindlay on 2006-09-02
I had problems with the live cd on an old laptop, and found that the text install was much better on it. Also, if you're going to sonly use it as a server, you don't need X installing, so ubuntu will be pretty much just as good as any other distro for what you want!

Hope this helps

---

### Post by taurus on 2006-09-02
Yipe.  Should go with the server version since you only run some file server on it anyway...  And if you want some window manager or environment, use fluxbox instead!

---

### Post by benfindlay on 2006-09-02
Yes, or you could try xubuntu from the start, as it uses the xfce desktop which is very light weight.

However, you may as well just install ubuntu for now, because you can add desktops later via the command line using ```
sudo aptitude install xubuntu-desktop
```(XFCE)

or
```
sudo aptitude install ubuntu-desktop
```(GNOME)

or
```
sudo aptitude install kubuntu-desktop
```(KDE)

Then you can test it for yourself, although I'd strongly recommend against installing gnome or kde on your specs!

Hope this helps!

P.S. sorry if I'm stating the obvious to you here, just being thorough ;)

---

