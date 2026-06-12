---
title: "TOTALLY embarrasing question...  -blushes-"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-17
SOLVED

and not so embarrassing after all.  :P

ok.  i've been using ubuntu for a while now.  and i've only hit one snag that i couldn't figure out.  how do you turn the thing off?  like, in windows (i HATE that operating system...  personal preference), you have a start>>turn off>> shut down option.  that will COMPETELY turn off your system.  i don't see anything like that in ubuntu.  i can only log off, lock the screen, suspend, hibernate, and switch the user.  no shut down.  ideas?  (i've been doing forced shut downs in the few months i've used it, but my computer hardly ever gets turned off.)

---

### Post by Jagot on 2007-04-17
You should have a 'Quit' entry in the System menu which should allow you to shutdown.  Alternatively you could run this:

```
sudo shutdown -h now
```

---

### Post by bmagyarkuti on 2007-04-17
There are a lot of ways you can turn off your machine. For most, the System>>Quit... button brings a panel, that has a Shut Down option. Yet, in some cases (for example if you are using Xgl) it is not present. Yet after clicking the log out button and being delivered the login screen, you can press F10, which pops up a menu with a Shut Down, and a restart option.

If none of the above graphical options work, you can still deactivate you machine from the terminal with the

poweroff

command. You might need to write sudo before it, to gain administrative privileges.

---

### Post by tonyr1988 on 2007-04-17
You have Beryl or Compiz installed, don't you? :)

Don't worry - it's not confusion, it's a known bug. See if [this]("http://ubuntuforums.org/showthread.php?t=244662&page=3#24") helps you work it out.

---

### Post by lamalex on 2007-04-17
are you using XGL with compiz or beryl? there is a bug with that that is easily fixed by adding > cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie" to your startxgl.sh script. you can shutdown via terminal with ```
sudo shutdown -h now
```


EDIT: oh no you're all so fast! I never had a chance

---

### Post by locke.dragon on 2007-04-17
thanks you guys!  i AM using beryl and i noticed the problem right after i installed it.  DUH!  -smacks forehead-  i should have thought that it was beryl.  :P  but how do i get to startxgl.sh to add the extra lines?

EDIT

fixed it!  thanks!

---

