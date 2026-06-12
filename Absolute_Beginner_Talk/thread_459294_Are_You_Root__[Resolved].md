---
title: "Are You Root ?? [Resolved]"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-05-30
Hi Folks,

Just trying to run the following command :- $sudo apt-get install ttf-gentium ........ 
to install some additional fonts, and i get the following message :- E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root

What do I need to do ??? please advise...thanks in advance 
SteveS

---

### Post by Outrunner on 2007-05-30
Make sure you don't have any other application open that uses APT(like synaptic or Add/Remove programs)

---

### Post by blazercist on 2007-05-30
did you have synaptic open wen you were trying this?  does a reboot fix this?

---

### Post by Brunellus on 2007-05-30
> **steve-shinn said:**
> Hi Folks,

Just trying to run the following command :- $sudo apt-get install ttf-gentium ........ 
to install some additional fonts, and i get the following message :- E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root

What do I need to do ??? please advise...thanks in advance 
SteveS
something is using the apt lockfile. you may be running apt/aptitude in another terminal window somewhere.  Wait for it to finish.

Alternatively, you might still have the "update-manager" running.  Wait for that to finish.

Also, you could have synaptic running.  Close that.

---

### Post by steve-shinn on 2007-05-30
Hi again,

Rebooted the pc just to make sure northing was running ..... ran the command again and still geting the same message ?? any advise welcome.

Thks in advance SteveS

---

### Post by Brunellus on 2007-05-30
you probably didn't sudo it.  Things that affect your system directories need root (superuser) privileges, which you get (temporarily) using sudo.  

For a better explanation see [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-05-30
Can you try pasting this command into the terminal? ```
sudo killall dpkg
```

---

### Post by daimaru on 2007-05-30
try typing 
```
sudo -i
``` 

should make you root (should show in command prompt or by typing whoami) then type 
```
apt-get install whateverUwantToInstall
```

if it still does not work ...

---

### Post by jkeyes0 on 2007-05-30
If what aysiu suggests does not work, you might have to go into a terminal and type
```
sudo rm /var/lib/dpkg/lock
```

This will delete the lock file in the dpkg directory. It's not pretty, but it gets the job done.

---

### Post by steve-shinn on 2007-05-30
Thanks guys got it sorted now ........

---

### Post by Brunellus on 2007-05-30
> **jkeyes0 said:**
> If what aysiu suggests does not work, you might have to go into a terminal and type
```
sudo rm /var/lib/dpkg/lock
```

This will delete the lock file in the dpkg directory. It's not pretty, but it gets the job done.
this should be a LAST resort, folks.

---

