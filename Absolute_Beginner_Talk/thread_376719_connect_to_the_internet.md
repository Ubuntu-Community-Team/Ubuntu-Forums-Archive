---
title: "connect to the internet ????"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-05
im trying to connect to the internet and i did all the "sudo pppoeconf" and i finish the process . after that i opened the terminal again and wrote on dsl-provider.
i get a message: "so. loaded".
i open the mozilla and i dont see it works what should i do?

*one more thing. now im in xp. usually when im restart i do the next stupid process: open device manager see my lan card is with "!" im disable it and that enable it . and only then i can coonect.
 hi. i entered the ping "72.14.207.99" and it give me the next message :"from 10.0.0.138 icmp_ seq=1 destination net unreachable."

---

### Post by Stemp on 2007-03-05
After pon dsl-provider, look at the pppoe logs using the command :

```
plog
```

may be there is something wrong (password, etc...)

nb : you may have to type plog several times.

---

### Post by fanny on 2007-03-05
thanks man . another problem is solved.

---

