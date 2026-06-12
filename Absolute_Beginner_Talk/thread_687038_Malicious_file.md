---
title: "Malicious file?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-03
Ack, please delete, just saw note re: not posting potentially malicious commands

---

### Post by TheBoat on 2008-02-03
The post refers to people giving bad advice and trying to get other people to execute malicious code.  However, if you have a question and you specify that you are talking about malicious code, you can certainly ask it.

---

### Post by ecs_pf5 on 2008-02-03
Figured it was safer to play safe ;) and really, I guess it's not directly Ubuntu - related.. I was just curious about a particular set of Linux - ish commands..

It was just a post to ask exactly what this file, found to have appeared in the root directory (public_html) of my webserver, would have done had it  ran successfully:

```

#!/bin/sh
echo Content-Type: text/plain
echo
rm -f $0
du -sh -- "../." | awk '{print $1}' 

```

I deleted it off the server pretty quick, and everything seems to be intact.. but the rm -f bit worried me a bit, especially since I never put the file there myself!

---

### Post by nick_h on 2008-02-04
This isn't anything to worry about.

The parameter $0 will contain the name of the file being executed, so it will delete itself when run.

The echo commands just write text.
The du command will print disk usage and the awk command just displays the first column of output (the size of the disk space used).

---

