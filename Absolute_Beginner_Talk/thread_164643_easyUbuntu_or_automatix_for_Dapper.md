---
title: "easyUbuntu or automatix for Dapper?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-23
Hi,

Just installed Dapper beta...wondering if EasyUbuntu or Automatix can be used under Dapper or there simply isn't any such programs for Dapper yet.

---

### Post by nalmeth on 2006-04-23
bumps multimedia script by iandefor might do what you're looking for
[http://www.ubuntuforums.org/showthread.php?t=138889](http://www.ubuntuforums.org/showthread.php?t=138889)

---

### Post by dermotti on 2006-04-23
I used that script but some reason i still dont get sound from videos......

---

### Post by unbuntu on 2006-04-23
Thanks for the pointer.

However, when I ran bumps, it complains that cannot find command  logsave.  I guess it hasn't been installed, and when I apt-get install logsave, it's not in the repository.  I think my source.lst may not have enough locations.  Is there a recommended source.lst for dapper also?

---

### Post by nalmeth on 2006-04-23
hmm, I never had that problem with bumps
you might try an older version, as I believe there are two you can download. Just delete the old folder and run the new one.
Check the dapper development release section, it's on the main page, if you haven't.
I think other's have made similar scripts for dapper. Bumps has been great for me so far, although it was buggy at first. Also with changes with dapper nearing release, iandefor probably has to do a lot to keep up.
The repos you have should all be fine to start with, just uncomment any thing thats, commented :)
BTW, did BUMPS ask you to keep new sources.list or restore the old one? If so, you may like PLF repositories.

---

### Post by unbuntu on 2006-04-23
Ya, it did ask me if I want to keep their source.list after installation failed, but I checked, it's still my old one.  I've copied their source.list.bumps into my /etc/apt/source.list, and now it seems I can have access to more packages.  But still no "logsave"...anyhow, I'll try again later.

P.S. damn, it's 6 o'clock already...

---

### Post by unbuntu on 2006-04-23
As a follow-up:  I've found logsave command.  It's installed with the base system, and it's under /sbin.  bumps didn't find it because sbin isn't in the $PATH environment variable.  Adding /sbin to the environment variable makes it work.

---

