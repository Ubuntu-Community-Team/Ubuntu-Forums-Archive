---
title: "&quot;Database Locked - Adept Updater&quot;"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by GrantShoe on 2007-03-04
I have been playing around with my brand new (as of this morning!) install of Kubuntu and i was just playing around with installing Java5 but it froze on 20% (for over 45 minutes).  so i tried to manually install and that didn't work and now adept won't open up and the adept updater won't either.  all i get is:
[quote]Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

i'm guessing it's that java install but i just restarted and on restart, it came up with the same thing.  how do i find out what is using the database and close that application!

---

### Post by Nythain on 2007-03-04
sudo dpkg --configure -a
or
sudo aptitude clean

one of those fixes your problem, i forget wich one

---

### Post by GrantShoe on 2007-03-04
> **Nythain said:**
> sudo dpkg --configure -a
or
sudo aptitude clean

one of those fixes your problem, i forget wich one

the first one :D thanks

---

### Post by GrantShoe on 2007-03-04
you know... it worked but then i did that adept updater and it's trying to install 122 updates.  first update? java.

i saw in this thread: [http://ubuntuforums.org/showthread.php?t=295802](http://ubuntuforums.org/showthread.php?t=295802) to try to apt-get it in the konsole to get by the user agreement but when i try to do that in konsole, it tells me that
/var/lib/dpkg/lock  couldn't be locked because another process is using it.  and when i show details in the adpt updater, i see the blue screen.

how do i get around this?

---

### Post by j.miller565 on 2007-03-04
> /var/lib/dpkg/lock couldn't be locked because another process is using it

when it says that, you  should exit out of Adept manger because that's the other process which is using it. I presume you had Adept on when you tried to install java from the Konsole, am I right?

---

### Post by GrantShoe on 2007-03-04
yeah... i took from that other thread that i didn't need to close adept updater but i'll give that a try

---

### Post by claydoh on 2007-03-04
Also, sometimes this file, '/var/lib/dpkg/lock' gets left behind when Adept crashes, or somehow does not close cleanly.This is to prevent more than one package manager running at a time. You can remove that file if you are not running apt-get or adept, and you should be able to proceed.
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by j.miller565 on 2007-03-04
That's what always appears if you're trying to install something from the Konsole when you have Adept or Synapatic Package Manger on

yea that's quite true claydoh

---

### Post by GrantShoe on 2007-03-04
I got java installed manually and i'm re-running the Adept Updater.

thanks guys!


i love this place.  it makes (k)ubuntu SO much easier.  i used to play with OpenSUSE and the community wasn't nearly as supportive.  it was like i had to figure out the issues on my own to join their elite club... amazing.

---

### Post by j.miller565 on 2007-03-04
No problems GrantShoe!!

---

### Post by TCSG on 2007-05-31
GrantShoe - Thanks for linking to the java post, it made things a lot easier.

Nythain - Thanks for the command to fix my installer "sudo dpkg --configure -a".

---

