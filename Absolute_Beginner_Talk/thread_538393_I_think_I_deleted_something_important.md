---
title: "I think I deleted something important"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by jefft113 on 2007-08-29
Hey guys, I was trying to install a program from the root directory, it wasnt working so I tried to delete to directories i had created. i wanted to type:

rm -r /usr/local/stata10

instead i accidentally hit enter after

rm -r /usr

Now i cannot get it to boot to the username screen, instead it lists a bunch of things it boots and then stops.

I can go to the root menu however and get to the recovery. I dont know what is wrong or how to fix it. Anyone have an idea?

---

### Post by Hobo Joe on 2007-08-29
Does it give any errors when you boot in recovery mode?

---

### Post by jefft113 on 2007-08-29
There are not error messages, just brings up to the root command line. I think it deleted the system resources and Im going to have to just reinstall it all.

---

### Post by sumguy231 on 2007-08-30
If you really deleted a chunk of /usr/, you're probably better off reinstalling unless you have backups to restore from.

---

### Post by funrider on 2007-08-30
buddy, on my first day in a software company as an intern, my boss told me whenever i do rm, do it with rm -i

just want to say that there is something you can prevent in the future.

---

### Post by jefft113 on 2007-08-30
I appreciate the help, i am going to just reinstall it, just have to download and burn to a cd. 

What does the -i mean  if I use rm -i?

---

### Post by funrider on 2007-08-30
from the man page of rm:

       -i, --interactive
	      prompt before any removal

it will ask you something like "do you want to remove file xyz (y or n)" for every single file you are going to remove......yea it is annoying in the beginning......

once you feel more comfortable with this command, u can skip the -i part

another good habit is to rename the file instead of removing it, 

eg. mv  /usr/local/stata10 /usr/local/stata10_removed

that way u can always have a chance to undo the change

---

### Post by jefft113 on 2007-08-30
Ok, thanks for the heads up, Ive used rm many times, just never with anything important, now I know.

---

### Post by sumguy231 on 2007-08-30
Edit: Never mind.

---

### Post by splintercellguy on 2007-08-30
You could alias the rm command I think:

alias rm='rm -i'

---

### Post by dwhitney67 on 2007-08-30
Yes you did.  I hope you learn something from this experience.

---

