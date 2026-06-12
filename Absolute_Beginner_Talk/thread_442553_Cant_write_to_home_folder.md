---
title: "Cant write to home folder"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-13
I want to write to my home folder but it says I don't have permissions, but I am the only user

how do I write to it?

---

### Post by steve.horsley on 2007-05-13
There should never be any problem writing to your home folder. Can you post the out put of this command:
**ls -ld ~**

Just to make sure this is not a simple misunderstanding - you home folder is the folder with your username **under** the /home folder. The /home folder itself is not writeable by users. For instance, my home folder is /home/steve.

---

### Post by sethdotcom on 2007-05-13
> **steve.horsley said:**
> There should never be any problem writing to your home folder. Can you post the out put of this command:
**ls -ld ~**

Just to make sure this is not a simple misunderstanding - you home folder is the folder with your username **under** the /home folder. The /home folder itself is not writeable by users. For instance, my home folder is /home/steve.




Sorry I wasn't using the Home folder with my user name, it works thanks

---

