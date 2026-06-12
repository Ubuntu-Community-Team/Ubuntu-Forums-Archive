---
title: "clear terminal cache"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by mikeee52 on 2006-10-29
Help! I know you use the up arrow key to bring up previous terminal commands, but haw do you clear previous commands. Is there a way to do this?

THanks for the help.

---

### Post by llamakc on 2006-10-29
Do you want your shell to not keep a history, or just clear it out?

The history is stored in ~/.bash_history, and you can clear it with the command:

echo "" > ~/.bash_history

---

### Post by GStubbs43 on 2006-10-29
```
history -c
```

---

### Post by mikeee52 on 2006-10-29
Thanks

---

### Post by llamakc on 2006-10-29
> **GStubbs43 said:**
> ```
history -c
```

Sweet! I didn't know about that one. Thanks.

---

### Post by GStubbs43 on 2006-10-29
No problem guys!  :-D

---

