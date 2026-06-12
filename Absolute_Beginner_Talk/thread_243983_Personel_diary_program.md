---
title: "Personel diary program"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-08-25
My daughter want's to have a daily diary she can write things to on out ubuntu based system.  My problem is I don't know of a good program that would allow her to do this.  I am also assuming she wants it password protected or encrypted for privacy.  If any one could help me I would appreciate it.

Thanks in Advance

Donald Saunders
Hershey PA

AMD K6-III 450, 512MB Ram, 30GB HD, ATI AIW 7200 video

---

### Post by %hMa@?b&lt;C on 2006-08-25
you could just have her write in openoffice.org and make the file only read/write by her by changing the permissions.

---

### Post by mssever on 2006-08-25
If you set up a user account for her, then any program should work safely, as only she will know her password. She might also want to run ```
chmod 700 ~
```

The other advantage to using separate accounts for everyone who uses the computer is that they can do whatever they want in their account without affecting other users.

---

### Post by alienexplorers on 2006-08-25
Sounds good to me.  Never thought about setting up a seperate account.  Guess I was stuck in the old MS world where you just logged on and everone used the same account.

---

### Post by mssever on 2006-08-25
I just realized that I didn't explain this adequately. I believe the the default permissions in Ubuntu allow users to read, but not write, each others' files.

Doing chmod 700 ~ will change this. Here's what it means: chmod means change permissions. 700 is the specific permissions--full control for the owner, no access for anyone else. ~ is an abbreviation for your home directory.

Of course, anyone with sudo access can still do anything they want. By default, this is only the account created when you installed Ubuntu.

---

