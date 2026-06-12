---
title: "[SOLVED] Synaptic package manager  trouble"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-21
[[IMG]http://img27.picoodle.com/img/img27/9/9/21/t_Screenshot1m_8311bbc.png[/IMG]](http://www.picoodle.com/view.php?img=/9/9/21/f_Screenshot1m_8311bbc.png&srv=img27)
:(check th screen-shot... im a root user...:confused:

---

### Post by Kilz on 2007-09-21
> **nikoPSK said:**
> [[IMG]http://img27.picoodle.com/img/img27/9/9/21/t_Screenshot1m_8311bbc.png[/IMG]](http://www.picoodle.com/view.php?img=/9/9/21/f_Screenshot1m_8311bbc.png&srv=img27)
:(check th screen-shot... im a root user...:confused:

Why are you runnig as root? You are aware that is a seriously a bad idea from a safty and security point of view.

---

### Post by RomeReactor on 2007-09-21
Hi. niko, are you sure you're running as root? maybe you meant that you're the only user on your system (if I'm not mistaken, if you were running as root your shell prompt would be **#** instead of **$**).

In any case, do what the system asks: that you run the command with superuser privilege (using sudo):
```
sudo dpkg --configure -a
```

---

### Post by nikoPSK on 2007-09-22
yes sorry I figured out the sudo part two minutes after I posted... But I still get the failed to write cache... heres a copy paste of what now says (I ran the dpkg --configure -a: )

E: The package wine-doors needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So, I guess I reported but I can't reinstall wine-doors. I only know how to use Gdebi package manager so I'm terible with tarballs. Also I can't install/ uninstall anything with terminal... Sorry I am having so much trouble lately.:(

---

### Post by nikoPSK on 2007-09-22
Apparently wine-doors needs to be re-installed but it works fine... And I keep getting a "corrupted package" and "mabye you don't have user rights/ privilliges" :confused:

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!!!

---

### Post by RomeReactor on 2007-09-22
Try running:
```
sudo apt-get install -f
```

If that doesn't work, try:
```
sudo apt-get remove --purge wine-doors
```

If it still won't work:
```
sudo dpkg --remove --force-remove-reinstreq wine-doors
```

---

### Post by nikoPSK on 2007-09-22
Thank you RomeReactor!

For the first two I kept getting:

E: The package wine-doors needs to be reinstalled, but I can't find an archive for it.

Then the last one worked. 

:):KS

Thanks alot, the forums are a great tool. (In the next release there should be a link to it under system tools...:popcorn:)

---

### Post by Raincheque on 2007-09-24
Amazing! RomeReactor, I had the hardest time installing virtualbox, and ended up with the same problem as niko. 
Thank you!

---

### Post by nikoPSK on 2007-09-24
I'm going to wait until at least version 2 is out. I'm marking this as SOLVED:)

---

