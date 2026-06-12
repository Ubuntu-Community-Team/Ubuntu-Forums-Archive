---
title: "Where do all those strange directory names come from?"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by stig on 2005-07-22
Hi,
When people like me first move from Windows to Linux they see a set of main directories with names like etc and opt. Some, like mnt and dev, seem meaningful but others like opt are not obvious. The less obvious ones are more difficult to associate with a function.

Is there a list somewhere explaining the origin of all these names and and how the name links with the function?
Thanks!

---

### Post by Lunde on 2005-07-22
Just google linux / unix directory structure

Here's one, there are lots out there:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by stig on 2005-07-22
Fredrik,
Thanks for the reply. I can find out what the directories are for, but the problem is why do they have these names? For instance, why is etc called etc? To me, "etc" means "et cetera" - is this something to do with the choice of the name?

I have tried googling for the words linux directory name, with the words "meaning" and with "definition" but nowhere can I find an explanation of why these names were chosen.

---

### Post by Kvark on 2005-07-22
They have short strange names because computer wizards love to save disk space by shorting words.

For example the .text file format was shorted to .txt which shaved a whole whopping character off the filenames and the command to change password was shorted to passwd which saves two whole keystrokes.

Many of the short forms feels completely random for us normal mortals who don't know on beforehand what they are shorts of. But in the minds of the computer wizards it is just as clear as if they had wasted 2-3 extra keystrokes to use the whole word.



But the directory structure is easy...
/home/yourUserName/ = all your stuff is in here, but ignore the junk with filenames starting with a dot,
everywhere else = You (almost) never need to go there, pretend the other places don't exist.

---

### Post by UbuWu on 2005-07-22
All of them explained:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

And indeed, etc comes from et cetera  ;-)

---

### Post by poofyhairguy on 2005-07-22
Some are shorted because the system was designed to be admined from a command line. Less to type.

---

