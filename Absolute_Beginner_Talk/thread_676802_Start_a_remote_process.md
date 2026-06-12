---
title: "Start a remote process"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by kikazaru on 2008-01-24
How can I start a process running on a remote computer, and have it continue after I log out?

For example, I can ssh from my laptop to my desktop, and thus start a slow download using bittorrent, but if I close the ssh connection then the bittorrent process dies... how can I start it in a way that keeps running?

Thanks!

---

### Post by Joeb454 on 2008-01-24
try using something like ```
(torrentclient &)
```

Where torrentclient is the application you want to run

that should launch it separately from the terminal.

I think you could use *screen* as well, but I'm not sure

---

### Post by kikazaru on 2008-01-24
Superb. You totally nailed it.Thanks!

I had no idea about that trick with the parentheses.

---

### Post by Joeb454 on 2008-01-24
No problem :) I use it all the time on my local machine, because it means I don't have to keep the terminal open :)

---

### Post by kikazaru on 2008-01-24
Sweet... now I can get back to absorbing  those family values while I download violence and sex in the other room.

:popcorn:

---

### Post by Joeb454 on 2008-01-24
:lolflag: Now now, lets keep the forums clean shall we ;)

---

