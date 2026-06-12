---
title: "i386 incompatibility?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by minacious on 2007-06-25
i installed xubuntu using alt. installer on an old box with 128 ram, 500mhz celeron. pretty much all of the applications in the ad/remove thing say "not compatible with i386", even ones like, say, freeciv, that worked previously with win98. why is this and can i change it?

---

### Post by yabbadabbadont on 2007-06-26
I would guess that the packages that aren't in the main repository were not compiled with i386 compatibility.  There isn't anything you can do to change it.  About the only thing you could do would be to try to compile these programs yourself, but I wouldn't recommend it unless you know what you are doing.  (you had to ask, so I doubt that you want to try this.  :D)  You might want to see about using Debian.  I think it still defaults to i386 compatibility for all of its packages, but I'm not sure.

---

### Post by minacious on 2007-06-26
the cd i used is called "xubuntu 7.04 i386"

---

### Post by yabbadabbadont on 2007-06-26
That doesn't mean that all the programs in the non-main repositories, especially the universe and multiverse ones, have been compiled for i386 compatibility.  ;)

I would guess that most of them have been built to require at least a i586.  (maybe even i686)

---

### Post by minacious on 2007-06-26
woah. *blinks*. all that stuff that wouldnt work, does with cd in drive. that solved problem i guess. ty for help

---

### Post by yabbadabbadont on 2007-06-26
Wait a minute... I just read your first post again.  You have a 500MHz Celeron processor.  That should be an i686.  Ugh.  Even though most of what I said was true, I don't think it applies to your situation.  There is something else weird going on here.  Don't give up on Xubuntu just yet.  Hopefully someone else will have an idea of how to help you.  I'm just sorry that I (unintentionally) mislead you.  :(

---

### Post by minacious on 2007-06-26
well, as i said, it allowed me to view and download apps with add/remove manager no problem, once i got the install cd in there. i just tried it again without cd and it works. ill attribute this to gremlins and keep using it. thank you for advice

---

### Post by ugm6hr on 2007-06-26
This issue is because you have to update package information on Synaptic - either from alternate CD (as a repository) or from the internet.  I'm assuming you didn't have internet access from the Xubuntu box when it wasn't working.  That explains the issue, I believe.  Not so much bug as inconvenience.

---

