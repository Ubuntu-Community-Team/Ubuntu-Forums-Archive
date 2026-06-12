---
title: "I shutdown Ubuntu while it was installing updates, now can't get passed login screen!"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-03-06
I shutdown Ubuntu while it was installing updates because I got a little impatient... and now after typing in my password and username onto the Ubuntu splash page, my computer remains at a completely cream colored background forever (freezes at time after login and loading of desktop)

Anyone know how to remedy this issue?

---

### Post by kesman on 2008-03-06
Try booting up to the recovery mode and then in the text-mode log in. Note that it may not let you see your password as you type it, thats normal. After this, run the following commands:
```

apt-get update
apt-get dist-upgrade

```
if they create errors, try to run this first:
```

apt-get -f install

```

When you are in recovery mode, you are logged in as root, so you won't be needing sudo in front of any command.

---

### Post by Arthur Archnix on 2008-03-06
What!?!? dist-upgrade? Why???

I disagree vehemently.

---

### Post by inktri on 2008-03-06
what do you suggest i do then?

---

### Post by kesman on 2008-03-06
He was performing dist-upgrade and then shut the computer down, that's why I'd suggest to perform dist-upgrade. Note that dist-upgrade isn't the same than just upgrade or upgrading the ubuntu version to the newest.

---

### Post by Arthur Archnix on 2008-03-06
My understanding is that the dist-upgrade command will upgrade your system to the newest version of ubuntu. If that's what you were trying to do then no problem. If you were simply installing updates though it would pretty much hose your current system, especially if you're on gutsy, because then you'd be running alpha software (Hardy). 

Instead of logging in, try switching to another terminal (Alt+F1) then
```
sudo apt-get -f install
```Then try logging in. If you still can't switch back to F1, then do:
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```
> 
He was performing dist-upgrade and then shut the computer down, that's why I'd suggest to perform dist-upgrade. Note that dist-upgrade isn't the same than just upgrade or upgrading the ubuntu version to the newest.

Sorry, Kesman, I don't see anything in his post about performing a dist-upgrade.

---

### Post by kesman on 2008-03-06
man apt

apt-get dist-upgrade and apt-get upgrade are nearly the same, only some difference about handling the dependecies.

---

### Post by zxscooby on 2008-03-06
what will apt-get clean do exactly?

---

### Post by kesman on 2008-03-06
remove unneeded packages and clear the apt cache I'd think.
```

man apt

```

tells you all you need.

---

### Post by kpkeerthi on 2008-03-06
> **kesman said:**
> man apt

apt-get dist-upgrade and apt-get upgrade are nearly the same, only some difference about handling the dependecies.

Exactly.

Also dist-upgrade will NOT upgrade to the newest version of ubuntu (hardy?) unless the repository is changed in sources.list file manually. Or atleast you need to do something similar to [this]("https://help.ubuntu.com/community/GutsyUpgrades")

---

### Post by Arthur Archnix on 2008-03-06
**Kesman**, I've read the man page and dist-upgrade isn't that scary. But it used to be the case that running that command on an Ubuntu system meant it was upgraded to the next version. 
> apt-get dist-upgrade - upgrades the entire system to a newer release. The same as the above, except add the “smart upgrade” checkbox -- i.e. tell APT to do whatever it has to do to upgrade to the latest packages, even if it means removing some other packages. (NB this is not a recommended way of upgrading to a new release)

See [here]("https://help.ubuntu.com/community/AptGetHowto"). Now, perhaps that's no longer the case, but it remains there in the community documentation, and if this user is running LTS this could present some problems. 
[B]
zxscooby,[/B] apt-get clean removes downloaded packages. So if some of them were broken because they were downloading and then he turned off the computer, this will get rid of the broken packages (all packages actually) and make apt-download them again. It's not bandwidth friendly, but it's easy.

---

### Post by kesman on 2008-03-06
Whoah, I've used Debian somewhere around 2001,later switched to Ubuntu, and dist-upgrade ALWAYS has only updated the packages, not the system. That must be VERY old info, or then faulty, since I've always ran dist-upgrade, from Ubuntu 5.04 to 7.10 and always only get my packages up-to-date.

---

### Post by Arthur Archnix on 2008-03-06
> **kesman said:**
> Whoah, I've used Debian somewhere around 2001,later switched to Ubuntu, and dist-upgrade ALWAYS has only updated the packages, not the system. That must be VERY old info, or then faulty, since I've always ran dist-upgrade, from Ubuntu 5.04 to 7.10 and always only get my packages up-to-date.

Well, it's not out of date, 
> last edited 2008-02-27 13:03:58 by Roshan5
But it certainly could be faulty. I don't know. I've never ran the command and like I said, the man page doesn't make it seem like there'd be any problems.

All the same, given that documentation, why not try update / upgrade first. Hopefully someone more familiar with apt-get dist-upgrade in ubuntu, and that page will be able to weigh in on the issue, because I'd sure like to know what it does.

Like kpkeerthi pointed out, the upgrade pages don't say anything about dist-upgrade.

---

### Post by kesman on 2008-03-06
I wonder if inktri ever got the machine working again.

---

