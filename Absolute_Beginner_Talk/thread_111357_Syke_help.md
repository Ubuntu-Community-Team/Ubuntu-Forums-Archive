---
title: "Syke help"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by lemmy999 on 2006-01-02
I' ve just installed Skype. The icon appears under Applications/Internet but clicking on the icon doesnt open the app.:( 
 How do i check whats happening? or is it a case of uninstalling and re-installing. If so how do i remove the app and start again?

---

### Post by drfalkor on 2006-01-02
run 'skype' in a terminal :KS

---

### Post by kaamos on 2006-01-02
Some versions of skype in different repos are a bit buggy. For me installing a .rpm from skypes site did the trick.. Was actually the only solution I found for this problem.

If you wish to do this, open a terminal and
```
sudo apt-get remove skype --purge
sudo apt-get install alien
wget http://www.skype.com/go/getskype-linux-qt32
sudo alien -i  skype-1.2.0.18-suse.i586.rpm
skype
```
This worked for me, hope it does that same for you.

---

### Post by lemmy999 on 2006-01-02
Kaamos

Tried it your way but am getting the following

skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Any thoughts?

---

### Post by kaamos on 2006-01-02
You are missing libraries. Try this:
```
sudo apt-get install libgcc1 libqt3-mt libstdc++5 
```

---

### Post by lemmy999 on 2006-01-02
Kaamos

Worked a treat- thanks mate!!:)

---

