---
title: "How to configure gnome, that &quot;firefox&quot; always opens on 2nd virtual desktop at startup"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by phibuntu on 2006-12-14
Hello

I am not realy new at Linux, but rather new at gnome. Probably this post belongs to a gnome forum?

Anyway
I want to configure my Desktop as follows:
I have 5 virtual screens. 
On the fist screen I want to have a terminal (with "midnight commander") started.
On the second screen I want to run firefox
and on the 3rd screen I want to have thunderbird.

I can store sessions, that the above mentioned applications open, but unfortunately they always open on the first virtual screen and midnight commander ("mc") is not started.

Any ideas?

---

### Post by xyz on 2006-12-14
Hi,
I have no ideas but you're lucky if this is your only problem!!
Is it really that important?
Cheers...

---

### Post by hotbrainz on 2006-12-14
Sounds like an awesome idea...I magine with 4 beryl desltops starting up with different applications....that will be really handy

Hope soemone find the way :rolleyes:

---

### Post by joselin on 2006-12-14
I don't know how to do it, but i wanted to suscribe this post. Hope that someone can answer your question.

---

### Post by phibuntu on 2007-01-03
It seams that "devils pie" does the job.

[http://www.ubuntuforums.org/showthread.php?t=75749]("http://www.ubuntuforums.org/showthread.php?t=75749")

I have not tried yet. But I will post further questions to the above metioned thread.

By the way: I found the solution first at a gnome forum :-)  :

[http://www.burtonini.com/blog/computers/devilspie]("http://www.burtonini.com/blog/computers/devilspie")

Syntax:
[http://xlife.zuavra.net/index.php/48/]("http://xlife.zuavra.net/index.php/48/")
[http://wiki.foosel.net/linux/devilspie]("http://wiki.foosel.net/linux/devilspie")

---

### Post by MiCovran on 2007-01-03
> On the fist screen I want to have a terminal (with "midnight commander") started
> midnight commander ("mc") is not started
For terminal applications to run in new terminal window, use "gnome-terminal -x", not just a command to start that program, try:```
gnome-terminal -x mc
```

---

### Post by phibuntu on 2007-01-03
Thanks MiCovran.

Now I have exactly what I want.

[LIST=1]
[*]I installed "devilspie" via synaptic.
[*]Added two config-files into ~/.devilspie to move firefox in fullscreen mode to the 2nd virtual desktop (workspace) (and same to thunderbird to the 3rd workspace).
[*]Added the devilspie, to the default session
[*]Added "gnome-terminal -x mc" to the default session
[*]Added firefox and thunderbird to the default session
[/LIST]

GREAT. Thanks you all folks :-D 

(here the two devilspie files:

```
(if (is (application_name) "Firefox") (fullscreen (set_workspace 2)))
```
and
```
(if (is (application_name) "Thunderbird") (fullscreen (set_workspace 3)))
```

---

