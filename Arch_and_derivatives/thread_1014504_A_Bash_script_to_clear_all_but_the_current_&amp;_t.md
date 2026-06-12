---
title: "A Bash script to clear all but the current &amp; the superseded packages from cache?"
date: 2008-12-17
forum: Arch and derivatives
---

### Post by handy on 2008-12-17
Has anyone written, found such a script, or like to write one? :-) 8)

It just has to delete all older duplicate packages in */var/cache/pacman/pkg/* .  After which keeping a superseded copy of packages just comes down to when you use the script.

It would keep the */var/cache/pacman/pkg/* directory slimmer, (though it would still have more than is required in it I know) & ensure a quick recovery through downgrading to a known good package when required.

It would be so easy to run the script before an -Syu --aur  so that if you have any problems you still have the superseded version of whatever, that you can downgrade to until the problem is solved.

(The title of this thread is incorrect, sorry about that.)

---

### Post by handy on 2008-12-18
Well, I'm displaying my natural slowness to the world again. :lolflag:

*pacman -Sc*

does what I need, it leaves only the packages that I am currently using in the cache, it also offers the user the opportunity to delete all of the unused repositories that have been accumulating in */var/lib/pacman/* .

I only need to keep the last known good packages so if/when a problem comes in I can downgrade if I have to, then when the problem(s) are sorted I can do away with the cache.

I thought the idea was so good that the Pacman people really should have done something about it by now. :lolflag:

The answer came courtesy of long suffering Allan an Arch dev'/mod' on the Arch forum.

---

### Post by mips on 2008-12-18
> **handy said:**
> Well, I'm displaying my natural slowness to the world again. :lolflag:

*pacman -Sc*


I thought the idea was so good that the Pacman people really should have done something about it by now. :lolflag:

Lol, when I read the first post I was wondering what complicated task you wanted to perform with a script. I was thinking packman -Sc or pacman -Scc but thought you wanted something else :)

---

### Post by MisfitI38 on 2008-12-18
Oh.
You mean *that*.
Yeah, ```
pacman -Sc
```
:P

---

### Post by handy on 2008-12-18
Yeh.  I stuffed up the title just to confuse you (& me) even more. ;-)

I seem to have the ability to make a simple thing complicated, sometimes... :lolflag:

---

### Post by handy on 2008-12-19
Here is a great thread for scripts to handle the pacman cache:

***_[http://bbs.archlinux.org/viewtopic.php?id=29555](http://bbs.archlinux.org/viewtopic.php?id=29555)_***

---

