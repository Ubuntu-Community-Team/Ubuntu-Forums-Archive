---
title: "please help - cannot open mid/kar files with kmid - TOTALLY LOST"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2007-05-11
Hi there,

I've just installed KMid, and I've never been able to open files with it. The message I get is:

"Could not open /dev/sequencer.
Probably there is another program using it"

I've tried to close Amarok and all other programs, problem persists.

THANK YOU VERY MUCH for your help.

---

### Post by ajgreeny on 2007-05-11
Install **timidity** and **freepats** from the repos.  You can also add **timidity-interfaces-extra** if you want a simple gui

---

### Post by Korrontean on 2007-05-11
Thank you!

I'm downloading what you've told me, it'll take a while. Any idea about why KMid not working?

---

### Post by ajgreeny on 2007-05-11
No idea, but I've never got it to work either.  You'll find a lot of other similar complaints in the forum as well.

---

### Post by Korrontean on 2007-05-11
The installations seems to be completed, BUT

1) I cannot select a file and then "open with" timidity, it's not on the list.

2) There is no access to timidity in the menus neither.

I type "timidity" in the console and I get the message about the copyright and so on. But I cannot open the program!

THANKS!

---

### Post by Romin-1 on 2007-05-11
I'll give this a bump 'cause I'm having exactly the same problems.

Good luck,

Jon

---

### Post by gustavocm on 2007-05-11
try
**timidity name-of-file.mid**

:guitar:

---

### Post by ajgreeny on 2007-05-12
Or if you installed **timidity-interfaces-extra** try starting it with the command **timidity -ik** (or **-ig**).  This will give you the simple gui I mentioned and make everything a bit easier, though the command line **timidity name_of_file.mid** will do it as well.

---

