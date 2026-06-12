---
title: "Weird Error When I Try to Apt-Get something..."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-26
Whenever I type **sudo apt-get install *filename*** I get the following error:

```

syndacate@syndacate-desktop:~$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
php5 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  noip2: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

At first I just thought it was one program, but now it doesn't work for anything, I tried to "reinstall" php5 because I knew I already did it once and it worked fine...but it's giving me the same error too.  It gives this error no matter what.

**apt-get -f install** gives the same errol.  Anybody have any idea what's up?  This just started.

This is the error I get when I go to **applications >> add/remove**:
```

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

```

EDIT:
**I found the problem**
I was typing **sudo apt-get install -f php5**

I tried **sudo apt-get install -f** and it un-installed noip2

Then I typed **sudo apt-get update** and it updated (it wasn't updating before).

Then I clicked **"applications >> add remove"** and it worked fine.

Anybody know why this happened, and if I can install noip2 again?  Typing IP's blows...

---

### Post by PeterJS on 2007-12-26
Looks like the issues from here never got resolved
[http://ubuntuforums.org/showthread.php?p=4010713](http://ubuntuforums.org/showthread.php?p=4010713)

Looks like noip2 is half installed and causing a mess.
Try giving
sudo apt-get remove --auto-remove noip2

---

### Post by khgiese on 2007-12-26
It sounds as if an update corrupted. Not sure if you can do the following:

sudo apt-get update
sudo apt-get upgrade.

If you can use those commands it should update your server list and then pull down any upgrades your system may need.

---

### Post by PeterJS on 2007-12-26
We'll see, but I don't think reloading the package list is going to do any good the offending package (noip2) was hand installed from the vanilla debian repositories.

---

### Post by Hospadar on 2007-12-26
probably you had a partial update, and it picked up the newer versions of some packages, but not of libc6, so then those packages couldn't find libc6.  That'd be my guess.  You might also try going into synaptic and having a gander at the "broken package" filter and see if anything obvious turns up there.

---

### Post by Syndacate on 2007-12-26
Well now that I did the install -f deal and it uninstall noip2, you guys know of any other domain name masks?  LoL - IP typing is a pain :(

PS:

NVM I think...
The domain name still works, lol, even though noip2 isn't installed...Weird...I thought no-ip client local was the only way for it to work...

---

