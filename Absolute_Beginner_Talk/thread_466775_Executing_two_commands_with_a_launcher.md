---
title: "Executing two commands with a launcher"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by stealth_monkey on 2007-06-07
Hi guys, as the title says, I was wondering if it's possible to create a launcher to execute two commands when activated. Specifically, I want to be able to launch beryl and beryl manager (commands beryl & beryl-manager respectively). What would be the syntax to do this, if possible

---

### Post by Inxsible on 2007-06-07
you would have to create a shell script and execute it

---

### Post by stealth_monkey on 2007-06-07
Thanks, any suggestions where to go to learn how to do that?

---

### Post by Inxsible on 2007-06-07
i was actually searching the forums for a link...but cudnt find one. let me see what else i can come up with

---

### Post by buuntuu! on 2007-06-07
linuxcommand.org for starters, follow my signature :)

---

### Post by Inxsible on 2007-06-07
Here's a helpful link

[http://www.hsrl.rutgers.edu/ug/shell_help.html](http://www.hsrl.rutgers.edu/ug/shell_help.html)

---

### Post by Inxsible on 2007-06-07
Something like

```
#!/bin/sh
beryl
beryl-manager
```

---

### Post by stealth_monkey on 2007-06-07
Thanks guys, playing with it now- for future reference, found a great guide (don't know if it's out of date, but it works for me)

[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

---

