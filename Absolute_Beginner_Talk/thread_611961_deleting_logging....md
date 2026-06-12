---
title: "deleting logging..."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Nikitas350 on 2007-11-13
I have a question about the file /var/log/messages. Does ubuntu delete it automatically? And if it does it how can i undo it? Thanks.... :)

---

### Post by taurus on 2007-11-13
You can empty it with

```
sudo cat /dev/null > sudo /var/log/messages
```

System won't delete /var/log/messages.

---

### Post by Nikitas350 on 2007-11-13
Thanks. I don't want to delete it. I want to keep it. I made a script in order to view how many calls i have done to the internet and how much time i was in the internet ( i have ISDN). The data was taken from the file /var/log/messages so i wanted to keep this file... ;)

---

