---
title: "rescueing ubuntu?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by theratwonder on 2007-05-04
This page [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/rescue.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/rescue.html) says that all you have to do is load off the install disk and put in "rescue" at the "boot:" prompt.

But, when i load the install disk it provides me with a number of options, and if I press f6 then I get a list of the boot commands, but putting "rescue" on the end of any of them doesn't seem to make an difference.

I tried pressing "esc" which takes me to a single "boot:" prompt, but when i type "rescue" in there it just says "image not recognised" or something.

Can someone help me? How do I access the rescue installation?

Ta.
Robin.

---

### Post by amaroKer on 2007-05-04
What are you trying to fix?

---

### Post by theratwonder on 2007-05-04
I'm trying to fix this problem for a friend:

When I boot up ubuntu it gets to the login screen fine, but then if I log-in with a valid username and password, the login screen disappears, and the screen goes blank for a bit, as if it's about to log me in, but then the login screen appears again.

I have managed to boot ubuntu live from the CD, but I don't have the first clue where to start looking to fix it. Isn't there some standard rescue disk thing that will just analyse your installation and fix errors / resolve dependencies / whatever?

---

### Post by Drakkor on 2007-05-05
Image backups are a wonderful thing, you just restore the working image,and you're good to go ! 
Evidently your friend hosed something, maybe go for a clean install ?? :)

---

### Post by theratwonder on 2007-05-05
Are some sort of image backups stored automatically in ubuntu? Could I find and restore one?

---

### Post by mcduck on 2007-05-05
> **theratwonder said:**
> Are some sort of image backups stored automatically in ubuntu? Could I find and restore one?
sorry, the answer for both is no. You need to do such backups manually, or get some program that would do it. Image backups take _much_ disk space, it really is not something to do by default.

Anyway, to solve the actual problem you should first try getting rid of all configuration files in that user's home directory. Just browse there, and create a zip of all files & directories starting with a dot. (Those files are hidden by default, you need to press ctrl-h in nautilus to see them, or use 'ls -a' in terminal to see them in file listings.).

That should solve the problem if any of those files had some error that caused the login to fail.

---

### Post by boudreaujr on 2007-05-05
Don't forget if you need to get into a terminal to bypass the gui to cntrl alt F2 and login from a plain terminal.  That might help get you pass your gui problem initially.

Good Luck.
Denis

---

### Post by theratwonder on 2007-05-05
Ta guys, being such a newbie at linux i didn't know how to get to the text terminal. That was really helpful.

Once in there (I'm quite proficcient at unix) I quickly discovered the problem:

The disk was absolutely full, and I would assume this means that the GUI couldn't store files it needed in swap or something, so it just gave up.

I just deleted a couple of movies and now it works fine.

Thanks guys.
Robin.

---

