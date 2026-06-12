---
title: "Jahshaka run problems"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by RankWeis on 2006-04-24
So, this is my first post here, I should just meniton that I've just started using linux, a bit by accident, and have very little clue of what's going on. I've managed to find out most of the problems I had during the installation of jahshaka, but now I'm confused, and I'm sure there's some simple solution to it...

but I ran this, and it outputed the following:

root@Home:~# dpkg -i jahshaka_2.0rc2.1-1_i386.deb
(Reading database ... 107243 files and directories currently installed.)
Preparing to replace jahshaka 2.0rc2.1-1 (using jahshaka_2.0rc2.1-1_i386.deb) ...
Unpacking replacement jahshaka ...
Setting up jahshaka (2.0rc2.1-1) ...

root@Home:~# 

I'm not exactly sure what happened, it gave no errors...but now I can't find how to run jahshaka. It's not in the "Sound and Video" category...and I tried running "jahshaka", but still nothing. Have I forgot to compile a part of it, or something? Thank you for your support in advance.

---

### Post by Nikusan on 2006-04-24
[QUOTE=RankWeis]So, this is my first post here, I should just meniton that I've just started using linux, a bit by accident, and have very little clue of what's going on. I've managed to find out most of the problems I had during the installation of jahshaka, but now I'm confused, and I'm sure there's some simple solution to it...

but I ran this, and it outputed the following:

root@Home:~# dpkg -i jahshaka_2.0rc2.1-1_i386.deb
(Reading database ... 107243 files and directories currently installed.)
Preparing to replace jahshaka 2.0rc2.1-1 (using jahshaka_2.0rc2.1-1_i386.deb) ...
Unpacking replacement jahshaka ...
Setting up jahshaka (2.0rc2.1-1) ...

root@Home:~# 

I'm not exactly sure what happened, it gave no errors...but now I can't find how to run jahshaka. It's not in the "Sound and Video" category...and I tried running "jahshaka", but still nothing. Have I forgot to compile a part of it, or something? Thank you for your support in advance.[/QUOTE]

Try running:
```
dpkg -L jahshaka
```

This will list all of the files "owned" by that package, it may give you a clue to run it. If that list is too big try:
```
dpkg -L jahshaka | grep bin
```

---

