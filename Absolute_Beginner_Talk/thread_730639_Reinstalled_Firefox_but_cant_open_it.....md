---
title: "Reinstalled Firefox but cant open it...."
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-21
I have reinstalled Firefox beta 4 and when i open it , it says process is already running. I restarted my system and when i opened it again , it says the same. What should i do now?

---

### Post by FreewareFan on 2008-03-21
While it's not a fix, it might be a short term solution to your problem.  Fire up System Monitor, and see if you see a firefox process.  If you do, then terminate the process, and then try to start firefox.  Might just work...

---

### Post by adi_das on 2008-03-21
no process named firefox. i also used terminal but it says no process

---

### Post by FreewareFan on 2008-03-21
Well, at this point, might I suggest that you install Swiftweasel 3 beta 4 instead? I just installed it yesterday, and it is GREAT!  Very fast, very stable, and it is, after all, just Firefox that's been optimized for Linux...  You might consider giving it a try..

[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

---

### Post by konungursvia on 2008-03-24
I am having the same problems with FF 3 beta 4 in a new Hardy install, but only after I used flyback to restore the old home settings from feisty. I can run FF using a shell and typing "sudo firefox" with password, but this is strange.  At about the same time I did this I enabled desktop effects in compiz, don't know if that was relevant. A side note: now deluge won't work any more. The deluge problem was why I upgraded to hardy! hehe. Anyone having this issue, and see why it's happening? Thanks.

---

### Post by konungursvia on 2008-03-25
Solved it for now, provisionally, by installing swiftweasel.

---

### Post by konungursvia on 2008-04-21
> **konungursvia said:**
> Solved it for now, provisionally, by installing swiftweasel.

Solved my problem: installing the rc6 then allowing updates, cause my home/user directory or parts of it not to be moded to 755, so many apps, including FF and frostwire, couldn't write to settings directories, due to lack of permissions. Did chmod 755 and chown user /home/user in root terminal and voila, it all works now.

---

