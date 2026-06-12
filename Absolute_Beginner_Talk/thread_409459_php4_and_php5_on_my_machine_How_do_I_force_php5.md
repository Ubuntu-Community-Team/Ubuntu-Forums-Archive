---
title: "php4 and php5 on my machine? How do I force php5?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by the_Reverend on 2007-04-14
Ok, this is going to sound weird, and I'm not 100% sure how this happened, but it looks like both PHP 4 and PHP 5 are installed on my machine.

I had thought to just reinstall php5, but when I use the command
```
sudo apt_get install php5
```
I get the notice that an important application (zoneminder) will be uninstalled automatically.  I really don't want this to happen.

So, how do I force the useage of php5 and just ignore the php4 core?

Is it possible?

J.

---

### Post by Seisen on 2007-04-14
You can try this and see if it will remove PHP 4 if you don't need it.

```
sudo aptitude remove php4
```

---

### Post by the_Reverend on 2007-04-14
I tried what you reccomended, and Ubuntu reports that php4 is all gone, and php5 is up to date.

But when I access my webserver (Apache), and go to a page that displays phpinfo(), php still reports version 4.

That's just crazy! :P

---

### Post by annda on 2007-04-14
i'd suggest you run

sudo updatedb
sudo locate php

that way you will see what php4 leftovers you have (maybe an old apache module) and what to remove manually. 

otherwise you can remove apache, php & co. from synaptic (complete remove with conf files) and install again.

also, aptitude has a -purge option that removes packages completely.

---

