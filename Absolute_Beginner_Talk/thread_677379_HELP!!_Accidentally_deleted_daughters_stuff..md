---
title: "HELP!! Accidentally deleted daughters stuff."
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Verbal_Kent on 2008-01-24
Ok, being a MS user...i made BoooBooo. I was moving my daughters folder over from my back up drive. Right after it was finished i realized i had moved it, not copied it...after selecting the folder again to copy back on to the back-up drive....i accidentally pressed delete.

Its not in my trash,.,,,someone wanna tell me where it sent it too. This will get me killed.


Oh, i am soaking wet behind the ears on Ubuntu,... just got it up today.:guitar: 

Thanks in advance,.

---

### Post by seventhc on 2008-01-24
I think you can open a terminal (applications>accessories>terminal)
type in ```
sudo nautilus
```
then on the right side click on file system. On the left side click on the home folder once that opens you should see her user name open that folder hit Ctrl-h to show hidden files look for .Trash
the path would be /home/HerUserName/.Trash
Notice the period in front of .Trash
from there you should be able to copy it and put it back.
hope this helps.

---

### Post by Verbal_Kent on 2008-01-24
I did that, but it didn't work, Thank you. It isn't in the trash for some reason.

I am using the Gutsy Gibson version of Ubuntu. I have two hard drives, one as a backup, only one username on Ubuntu, When i hit my <delete> key the folder vanished. It has all her house of mouse tivo's in there.....boy i will be a dead man (from the wife)

---

### Post by seventhc on 2008-01-24
hmmm, so only one user, and it isn't in your trash either. I'm sorry I'm not to sure then maybe someone here had a similar situation and will be of more help to you.

---

### Post by Verbal_Kent on 2008-01-24
> **seventhc said:**
> hmmm, so only one user, and it isn't in your trash either. I'm sorry I'm not to sure then maybe someone here had a similar situation and will be of more help to you.

All the stuff i right clicked on and "empty to trash" is in there. Not the few things i actually hit my <delete> key on my keyboard. Thanks for your help, i need some tums, ..... LOL..

---

### Post by theRightNee on 2008-01-24
hrm...since it contains tv shows, the folder would have been pretty large yes? if that is the case, it would have been "erased", not moved into the .trash folder. It is what happens to larger files. I am sorry, but I cannot think of any way to solve this issue...perhaps buy the show on DVD? Best of luck.

---

### Post by Paul820 on 2008-01-24
I don't know if this will work but there is no harm in trying [http://recover.sourceforge.net/linux/]("http://recover.sourceforge.net/linux/")

---

### Post by Verbal_Kent on 2008-01-24
Wow, no kidding. Its not something i can just go buy. These were like her 6-7 favorite episodes of the house of mouse cartoon. This is not good.

---

### Post by Verbal_Kent on 2008-01-24
> **Paul820 said:**
> I don't know if this will work but there is no harm in trying [http://recover.sourceforge.net/linux/]("http://recover.sourceforge.net/linux/")

I am giving it a run. Thanks!

---

### Post by Paul820 on 2008-01-24
This can recover video and photos so it might be a bit better than the last one [http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")
Best of luck to you!!

---

### Post by blastfm on 2008-01-24
Have you tried looking in to all the .Trash folders? These are hidden folders and isn't necessarily the same location as the what the Trash icon on the desktop is pointing to.

Open a nautilus window 

```
sudo nautilus
```

.. then go to the View menu and click on Show hidden files

On this same nautilus window try going around the folders and look for .Trash, .Trash-*username* and Lost+Found folders.

Best of luck in finding those files.

---

