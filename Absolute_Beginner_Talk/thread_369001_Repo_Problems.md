---
title: "Repo Problems"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-24
Hi. I keep getting the following error when I try to 'reload' in synaptic:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

> [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

I used firefox to download this package.gz file and it opened ok in archive manager...

Any suggestions as to what might be causing this and how to fix it?

-Thanks

---

### Post by dr_d on 2007-02-24
is anybody else having this problem? i would like to know if it's a problem with my box or with the repo server...

---

### Post by yabbadabbadont on 2007-02-24
I would test it for you, but I don't want to break mine too.  :D

Usually repo issues are resolved by waiting a few hours and then trying again.

---

### Post by dr_d on 2007-02-24
well it's been a couple of hours... still no joy. :( :( :( :( 

i'm considering moving to the main mirror as i've had problems with the australian mirror before.

---

### Post by dr_d on 2007-02-24
damn. i searched on google and it seems this is an old error.

[http://ubuntuforums.org/showthread.php?t=189456](http://ubuntuforums.org/showthread.php?t=189456)
[http://ubuntuforums.org/archive/index.php/t-427.html](http://ubuntuforums.org/archive/index.php/t-427.html)
[http://ubuntuforums.org/archive/index.php/t-427.html](http://ubuntuforums.org/archive/index.php/t-427.html)

iduno why it happened to me all of a sudden, but i really dont want to change my sources.list to ftp instead of http.... i'm tempted to reinstall edgy.. but if i did that and got the same error again i think i might do something rash (eg put a fist through my monitor).

---

### Post by dr_d on 2007-02-24
HORAY!!!! i fixed it! and i didn't resort to attacking my mouse with a screwdriver like last time :)

i was wondering why changing http to ftp was working for people and on a hunch i commented out my entire sources.list and reloaded. then i enabled it all again and what do u know, it worked!

i really should try to post this fix on all those other threads......

---

### Post by Kateikyoushi on 2007-03-10
What did you reload ? Tried to update ?

---

### Post by yabbadabbadont on 2007-03-10
> **Kateikyoushi said:**
> What did you reload ? Tried to update ?

> on a hunch i commented out my entire sources.list and reloaded. then i enabled it all again and what do u know, it worked!

That suggests that he commented out all the entries in his /etc/apt/sources.list, then ran "sudo apt-get update", then uncommented them and ran that command again.  That is the command you usually run whenever you make changes to the sources.list file.  ;)

---

### Post by omps on 2007-03-11
I hashed out the repositories in /etc/apt/sources.list and it worked. anyways i was having problems only with dapper-updates repositories so i hashed them out and it worked. as in my case it wasn't an important repo.  well, i presume changing to any mirror site can also help.

---

### Post by Sonicgoo on 2007-04-22
finally tried the FTP trick it worked! Thanks

---

