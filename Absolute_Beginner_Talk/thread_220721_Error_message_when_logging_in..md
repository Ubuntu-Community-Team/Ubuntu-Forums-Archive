---
title: "Error message when logging in."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by watto_one on 2006-07-22
I am getting the following message after I sign in. Any help on what is wrong and how to fix it please.

User $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 perrmissions. User's $Home directory must be owned by user and not be writable by other users.

Thanks in advance.

---

### Post by digby on 2006-07-22
It appears that something is wrong with your .dmrc file.  Try this:```
sudo chown your_user_name.your_user_name /home/your_user_name/.dmrc
chmod 644 ~/.dmrc
```
If that doesn't fix it, post the output of ls -l .dmrc

---

### Post by watto_one on 2006-07-22
Sorry to say it doesn't appear to have done anything. The message still appeared when I looged back in.
As requested here is the out put you required
-rw-r--r-- 1 peter peter 45 2006-07-11 09:55 .dmrc

---

### Post by professor_chaos on 2006-07-22
not sure if this help you but my permissions for that file is 600

---

### Post by watto_one on 2006-07-22
Please still answer if you know what is wrong

---

### Post by Dr. Nick on 2006-08-09
Try this

sudo chmod 750 /home/<username>/.dmrc

---

### Post by watto_one on 2006-08-09
Thanks Dr, I'll try this when I get home.

---

### Post by Dr. Nick on 2006-08-09
Hope it works, I just edited it to 750 as I heard that was safer

---

### Post by watto_one on 2006-08-10
Thanks again. The error message has gone.

---

