---
title: "need help with chmod"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by vvnoob on 2006-02-07
How i use chmod to get read write execute permissiom?

When i do [HTML]chmod 666 /var/www/ i can not write in that folder[/HTML]

Can anyone other strings?

tnx

---

### Post by kaamos on 2006-02-07
**If** you are the only user you can make you life easier with
```

mkdir ~/www
sudo mv /var/www /var/www_orig
sudo ln -s ~/www /var/www

```
The www folder is now accessible in your home directory.

---

### Post by earobinson on 2006-02-07
If you ever have problems with a command you can always man it.

To man a command you just do this ```
man command
```so in your case you could have done ```
man chmod
``` Oh ya FYI man stands for manual.

---

### Post by rmjokers on 2006-02-07
You need 777 to get read write execute permissions for all users.

---

### Post by vvnoob on 2006-02-07
Tnx 
Now i fixwd path in apache conf.file :-)

But in the future i may have need some other dir to allow rw permissions
it will be useful that i know strings for it.

TNX

---

### Post by vvnoob on 2006-02-07
[QUOTE=earobinson]
Oh ya FYI man stands for manual.[/QUOTE]

Well with me broken english im very happy to understand this simple explanations :) 

what means FYI i will not even ask :) 

TNX anyway everything work now.

---

### Post by earobinson on 2006-02-07
To bad you get an answer. FYI = for your information
PS I have not had any problems with your english so far :)

---

