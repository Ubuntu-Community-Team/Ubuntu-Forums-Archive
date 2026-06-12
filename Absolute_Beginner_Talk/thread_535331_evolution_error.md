---
title: "evolution error"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-26
Have configured evolution and am able to retrieve messages from my G-mail mail box...

However, while downloading my mails today, i got this error meaasge

Error while Fetching Mail.

Cannot get message GmailId11399fd4f563bf44: No space left on device

What does this error mean......

pkj

---

### Post by switlikbob on 2008-01-02
Same error here...

---

### Post by jken146 on 2008-01-02
Sounds like you might have run out of space on the partition where your mail is stored (it's usually in /home/yourusername/.evolution I think).  See what you get from ```
df -h
```

---

### Post by switlikbob on 2008-01-02
That was it.  Last week I ran a backup of my windows machine to my ubuntu machine.  That backup file filled up my drive.

---

