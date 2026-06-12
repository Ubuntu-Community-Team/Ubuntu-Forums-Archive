---
title: "Simple machines forum"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by yahn on 2007-07-01
I'm trying to install SMF on my computer, but It's giving me an error saying that I need to change the permissions of some files to 777 or, on some machines, 755.  I tried changing them to 777 first and then 755, but neither worked.  I did chmod permission fname, did I do something wrong?  Can anyone tell me if they know how to fix this. 

Thank you.

---

### Post by Raineer on 2007-07-01
What kind of failure are you getting? Is it still saying the permissions didn't change?

You might try:
```
sudo chmod 777 filename.txt
``` 
It could also be possibly referring to the directory itself and not the files.

Remember, always try sudo if the command doesn't seem to work right, as established in [this]("http://huntersdad.com/?p=22") comic.

---

### Post by sirius11 on 2007-07-01
how could you install SMF on your computer unless you have a Mysql database,  how could you have installed a mysql database without knowing how to Chmod a file or folder..

  you'll get more help in the SMF forum about this question.

---

### Post by yahn on 2007-07-02
Because MySQL comes installed. .  And I tried sudo.  I guess I'll have to try the SMF forum again.  I didn't get anything last time.

Thanks.

---

