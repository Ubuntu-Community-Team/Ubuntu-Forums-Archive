---
title: "Synaptic package manager in Kubuntu"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-09-28
Hi
a mate told me how to get it but I forgot, at the mo I only have Adept which i'm not used to yet.
Can someone tell me how to get synaptic like we have on ubuntu?

TA

---

### Post by Kateikyoushi on 2006-09-28
sudo aptitude update
sudo aptitude install synaptic

That's it

---

### Post by Jareth on 2006-09-28
I don't think that did it,
I can't see it anywhere and in the terminal it says (Along with other things):

No candidate version found for synaptic

That sounds to me like it hasn't done nuthin? It has tried but maybe it can't find it or something?:confused:

---

### Post by aysiu on 2006-09-28
Sounds to me as if something's wrong with your repositories list.

Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Jareth on 2006-09-28
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



I think even I can tell that doesn't look good?:-k

---

### Post by Kateikyoushi on 2006-09-28
Yes all those lines are commented.
Remove the # from the beginning of this line.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

---

### Post by Jareth on 2006-09-28
Cheers, you'll have to walk me through changing that though?

---

### Post by Kateikyoushi on 2006-09-28
sudo gedit /etc/apt/sources.list

Then remove the # from the beginning of these lines

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

Save it and try to install again.

sudo aptitude update
sudo aptitude install synaptic

---

### Post by Jareth on 2006-09-28
all im getting from that first bit is:

sudo: gedit: command not found

---

### Post by Kateikyoushi on 2006-09-28
Sorry I forgot you are on kde.

sudo nano /etc/apt/sources.list

---

### Post by Jareth on 2006-09-28
erm... how do I save it then?:-k

---

### Post by Kateikyoushi on 2006-09-28
CTRL+X then Y and finish with an enter.

---

### Post by Jareth on 2006-09-28
ok, looks like we changed something but still no synaptic even after doing the update first.

---

### Post by Kateikyoushi on 2006-09-28
I found it.
Then uncomment this line.

#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

synapric is on that repository.

---

### Post by Jareth on 2006-09-28
Lookin good now, thanks for all your help there...


You        Are         A         Legend!

---

