---
title: "Trying to update"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by apowell656 on 2007-06-15
Trying to complete a routine update but I keep recieving the following error:


> E: /var/cache/apt/archives/language-pack-gnome-en_1%3a6.06+20070601_all.deb: files list file for package `ekiga' is missing final newline


I tried to delete ekiga- since I never used it , but there are some dependencies any help would be appreciated.

Andre

---

### Post by dbbolton on 2007-06-15
> **apowell656 said:**
> Trying to complete a routine update but I keep recieving the following error:





I tried to delete ekiga- since I never used it , but there are some dependencies any help would be appreciated.

Andre
the package 'ubuntu-desktop' depends on 'ekiga', which is why it's not letting you remove it.

try running synaptic, searching for 'ekiga', then mark it for an upgrade, and click Apply.

---

### Post by apowell656 on 2007-06-15
Unfortunately the same error with -newline

---

### Post by dbbolton on 2007-06-15
hmm, ok. it's possible that this package is broken. if that's the case, you can fix it with this command:
```
sudo aptitude -f install
```

---

### Post by Kenji Mapes on 2007-06-15
I get a similar problem.  I[ posted a thread here. ]("http://ubuntuforums.org/showthread.php?t=469553") The one suggestion I did get did not solve the problem.  Additionally trying fix broken packages did not work.  I can't update, install libc header files or install nvidia drivers.:(

---

### Post by apowell656 on 2007-06-21
Just had a chance to try the option sent 
```
sudo aptitude -f install

```
and that did not work

Andre

---

