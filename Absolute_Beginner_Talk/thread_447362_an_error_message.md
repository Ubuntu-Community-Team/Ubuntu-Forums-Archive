---
title: "an error message"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ymasarwar on 2007-05-17
i am getting this error message, can anyone help me regarding this.

the error message is


[I]E: Malformed line 45 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

[/I]


can anyone help me out?

i am using Ubuntu fiesty fawn 7.04 and also a newbie to this wonderful land of linux.

any help will be highly appreciated.

thanks!

---

### Post by Bachstelze on 2007-05-17
```
sudo nano -w /etc/apt/sources.list
```

Go to line 45, You should find something interesting ;)

---

### Post by ymasarwar on 2007-05-17
oh sorry forgot to mention, i am getting this error when i am opening synaptics or update manager.

---

### Post by Hobo Joe on 2007-05-17
Type into the Terminal:

```

gksudo gedit /etc/apt/sources.list

```

Then paste the output, we'll fix it for you. :)

---

### Post by ymasarwar on 2007-05-17
line 45 is the last line here,

## Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty

---

### Post by Bachstelze on 2007-05-17
It is wrong indeed. What did you add it for ?

---

### Post by ymasarwar on 2007-05-17
i was looking for a dock and came to this site which gave me these instructions, thats it.


so what should i do now?:confused:

---

### Post by Bachstelze on 2007-05-17
Do you have a link to the instructions you followed ?

---

### Post by ymasarwar on 2007-05-17
here it is...

[http://osnovice.blogspot.com/2007/05/avant-window-navigator-dock-like-bar.html](http://osnovice.blogspot.com/2007/05/avant-window-navigator-dock-like-bar.html)


cant i just remove it :(

---

### Post by Bachstelze on 2007-05-17
Those two lines (the ones with tuxfamily in them) are OK, it's the last one that is the problem. You could just delete it, I guess ;)

---

### Post by ymasarwar on 2007-05-17
thanks alot guys, it worked!!!!!!!!!

---

