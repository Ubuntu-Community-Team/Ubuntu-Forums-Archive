---
title: "[SOLVED] getch() and kbhit()"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-03
Is there something like getch() or kbhit() that could be used in a bash script? I have written a script that I call using a launcher, but the CLI opens and closes immediately after the script is executed. So I want it not to end until the user presses a key.

---

### Post by Cypher on 2008-04-03
Use "read" to allow the user to hit the "ENTER" key to continue..

---

### Post by sayakb on 2008-04-03
> **Cypher said:**
> Use &quot;read&quot; to allow the user to hit the &quot;ENTER&quot; key to continue..

Thanks that works :)

---

