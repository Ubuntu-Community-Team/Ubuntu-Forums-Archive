---
title: "Copy file from 1 place to another&gt;is this correct?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-02-26
I want to copy a file called file1 on my desktop to another users (on the same computer) desktop. 

Is this the correct thing to paste into crontab? (or is it totally wrong to do this?)

# get CPU temps from meniscus desktop and post them on friends(user2) desktop
*/1 * * * * root cp /home/meniscus/Desktop/file1 > /home/user2/Desktop/file1

---

### Post by anaconda on 2007-02-26
havent used crontab, but the normal copy command is just:
cp /home/meniscus/Desktop/file1 /home/user2/Desktop/
so no ">" in between and no need to mention the file1 2 times...

---

### Post by renzokuken on 2007-02-26
i'd just use 

```
sudo cp /home/user1/Desktop/file1 /home/user2/Desktop/
```

---

### Post by meniscus on 2007-02-26
Thanks for that oringinal code

Im tryin to copy file1 over at 1 minute intervals because its being updated all the time.

Im using this code



```
*/1 * * * * root cp /home/meniscus/Desktop/file1 /home/user2/Desktop/
```

---

### Post by hannaman on 2007-02-26
What's the */1 notation for?  If you are doing 1 minute intervals you could just use all asterisks (* * * * *)

---

### Post by renzokuken on 2007-02-26
you could also create a script to do the copying and set cron to run that script every minute

---

