---
title: "Dns"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by voltage on 2007-02-26
Hi,

Do somebody can tell me how to verify the DNS service is installed at the Ubuntu box at terminal window?

Thx

---

### Post by halitech on 2007-02-26
from the terminal

```

ps -e |grep bind9

```

should tell you or just do

```

ps -ef

```

---

### Post by voltage on 2007-02-26
> **halitech said:**
> from the terminal

```

ps -e |grep bind9

```

should tell you or just do

```

ps -ef

```

is that also can display the bind is started ? if not can you please show me how to view the DSN is up. If DSN was not started, then how to make it start automatically while boot-up ?

---

### Post by halitech on 2007-02-26
the first command will tell you if bind is running. the second command will list all running apps.

if you need more info, check here

[http://www.ubuntuforums.org/showthread.php?t=236093&highlight=bind]("http://www.ubuntuforums.org/showthread.php?t=236093&highlight=bind")

---

