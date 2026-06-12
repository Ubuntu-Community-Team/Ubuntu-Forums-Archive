---
title: "Unable to execute &quot;/bin/sh&quot; for rcS: No such file..."
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by DiG3RATi on 2007-07-27
So, I popped my Ubuntu 'cherry', if you will... :biggrin:
Meaning I crashed my first box... pretty sure I mv'd something I shouldn't have.  ](*,)

Any way to do a quick repair on this or am I looking at full reinstall?

---

### Post by deadgobby on 2007-07-27
What command are you using to get that error? 

Gobby

---

### Post by DiG3RATi on 2007-07-27
> **deadgobby said:**
> What command are you using to get that error? 

Gobby

The command involving pressing the power button... 

I'm dead in the water.. Ubuntu no bootu...  ;)


Prior to the 'no bootu' I was attempting to extract and compile qemu and kqemu in /usr/local/src

---

### Post by Mornedhel on 2007-07-27
Bad move, that. Installing from packages is almost always a better option.

I'm guessing the rcS in question is /etc/default/rcS which contains variable settings used at boot time. From the manpage of rcS, I'd say to recover you need to copy /usr/share/initscripts/default.rcS to /etc/default/rcS (not the contents, the actual file, so permissions, ownership, etc. get transferred as well). Maybe do that from a live CD or something, since you likely cannot get very far into the boot process.

But I'm going on a limb there, could be completely mistaken, and lead to the utter, definitive and complete hosing of your Ubuntu.


Does anyone else have something on this ?

---

### Post by deadgobby on 2007-07-27
[http://ubuntuforums.org/showthread.php?t=377683](http://ubuntuforums.org/showthread.php?t=377683)
[http://ubuntuforums.org/showthread.php?t=322709](http://ubuntuforums.org/showthread.php?t=322709)

---

### Post by Mornedhel on 2007-07-27
OK, so I was indeed talking out of nowhere. (Sue me.)

The second thread failed to solve the problem (suggestion was to link /bin/sh to /bin/dash in case sh was the problem - smart, but apparently, sh was not the cause of the problem).

The first thread starts with a big "Solved", mentions something about testing kernel fixing the issue. Eh, I say good luck and report on your progress.

---

### Post by DiG3RATi on 2007-07-27
> **Mornedhel said:**
> Bad move, that. Installing from packages is almost always a better option.

I agree, however I was following [this How To:]("http://ubuntuforums.org/showthread.php?t=179472")... 

> **Mornedhel said:**
> I'm guessing the rcS in question is /etc/default/rcS which contains variable settings used at boot time. From the manpage of rcS, I'd say to recover you need to copy /usr/share/initscripts/default.rcS to /etc/default/rcS (not the contents, the actual file, so permissions, ownership, etc. get transferred as well). Maybe do that from a live CD or something, since you likely cannot get very far into the boot process.

But I'm going on a limb there, could be completely mistaken, and lead to the utter, definitive and complete hosing of your Ubuntu.


Does anyone else have something on this ?

I'll give 'er a shot... 

Thx..

---

### Post by DiG3RATi on 2007-07-27
HAHA!! I'm such an Ubu - newb...

I added a / before moving a qemu bin directory and ended up moving the root bin directory!

In honor of the Simpson's Movie opening today - DOH!!!!!   ](*,)


Note to self:  Donate heavily to Stephan Schreiber @ fs-driver.org!!!!  ;)

---

