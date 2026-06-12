---
title: "dpkg?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-01-02
How do you re set up the xorg.conf file using dpkg command? I have done this before, but can' remember what I typed.

Cheers.

---

### Post by cifdtruckie on 2008-01-02
Here ya go...

```
dpkg-reconfigure xserver-xorg
```

---

### Post by LowSky on 2008-01-02
sudo dpkg-reconfigure xserver-xorg

---

### Post by ~LoKe on 2008-01-02
This way:
```
sudo dpkg-reconfigure xserver-xorg
```
And this way, it will generate the file automatically:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cifdtruckie on 2008-01-02
Ahh, right... forgot the ubiquitous sudo

---

### Post by chrispche on 2008-01-02
Thanks for the prompt reply. Also any ideas on another problem I am having?

[http://ubuntuforums.org/showthread.php?t=655265&highlight=chrispche](http://ubuntuforums.org/showthread.php?t=655265&highlight=chrispche)

Thanks in advance.

---

### Post by ~LoKe on 2008-01-02
> **chrispche said:**
> Thanks for the prompt reply. Also any ideas on another problem I am having?

[http://ubuntuforums.org/showthread.php?t=655265&highlight=chrispche](http://ubuntuforums.org/showthread.php?t=655265&highlight=chrispche)

Thanks in advance.

I can't see a problem there.  Firestarter is just a GUI to configure IPTables (your firewall).  IPTables is running on boot by default, and the GUI is only necessary if you want to make changes.

---

### Post by chrispche on 2008-01-03
Yes but why the Firestarter fail message in bootup? It used to say OK. Look at my last post maybe you can see where I'm coming from.

---

