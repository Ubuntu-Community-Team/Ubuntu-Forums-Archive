---
title: "Is there a command to show past actions that have occured in the terminal?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-04
Yeah, so I'm trying to install Google Earth and I found this debian package:

[http://packages.debian.org/googleearth-package](http://packages.debian.org/googleearth-package)

After I installed it, in the upper right hand corner (I'm using Xubuntu by the way, I guess you'd call it the task manager in Winblows) it showed that there was an update to create a package called "googleearth-package" well I installed it but when I search for this file I can't find it. I thought that perhaps if I saw past things that have happened in the terminal I might be able to figure it out.

---

### Post by SIXAXIS on 2008-03-04
Press the up arrow key

---

### Post by wormser on 2008-03-04
Another option is the history command.  You can pipe it into less to read one page at a time.

```
history | less
```

---

### Post by whoscheesemine on 2008-03-04
> **SIXAXIS said:**
> Press the up arrow key

yeah sorry I didn't describe it very well, I didn't mean past commands that I've entered I meant past stuff that... uhh how can I word this... that the terminal has said to me?



I'll try the history thingy here in second...

Edit: Yeah that just gives me a history of the last 160 commands I've tried, thanks a lot though, I'm looking for something that will say all the things that like I said "Linux/terminal says to me"

---

### Post by Joeb454 on 2008-03-04
There's also a file in your /home directory :)

It's called **.bash_history** so you can see it by typing either ```
less ~/.bash_history
```

or

```
cat ~/.bash_history
```

---

