---
title: "How to view running processes in console?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-28
Thanks.

---

### Post by Celegorm on 2007-06-28
```
ps aux
```

---

### Post by hyper_ch on 2007-06-28
constant monitoring:

```

top

```

or I prefer this
```

htop

```
Installation: ```
sudo aptitude install htop
```

or you can look for something specific:

```

ps aux | grep apache

```

---

