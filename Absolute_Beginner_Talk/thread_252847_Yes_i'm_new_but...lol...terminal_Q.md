---
title: "Yes i'm new but...lol...terminal Q"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-07
Ok i'm interminal and put in this command "rmmod pcspkr"  and it says Operation Not Permitted...  I read something about super user somewhere but how do i do that... Thanks

---

### Post by pbaehr on 2006-09-07
To run a command as a super user preface the command with 'sudo'. For example, in your case:

```
sudo rmmod pcspkr
```

It will prompt you for your password (your regular user password) and then it will run the command as if you were root.

---

### Post by Omnios on 2006-09-07
Try
```

sudo rmmod pcspkr

```

 Sudo does commands as root

---

### Post by jd65pl on 2006-09-07
Try putting

```
sudo rmmod pcspkr
```

Oops too slow as above ;)

---

### Post by Devile on 2006-09-07
Perfect thanks guys...

---

