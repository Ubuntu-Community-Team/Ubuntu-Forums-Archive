---
title: "cant get write permission"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by hashslinger on 2006-12-19
If any one who reads this knows how to do what i am trying to do and knows how to do it please please please help me
t

i am trying to rewrite a conf file and i dont guess that i have mastered the use of the sudo command or the root user       i have read a bunch of documentation on how todo it and every time i try to it wont let me save my changes  i tried to rewrite the whole thing and just replace it and it would not let me  I am totally lost  i have only been using ubuntu edgy for a couple of weeks now and i cant say enough bout how much i am impressed with my first linux experience   i have never read so much in my life even bought the linux for dummies and that didnt even help me     also is there a way for me to change permissions on folders that have owner only axcess i havent been able to find any thing on this either  thx      ](*,)

---

### Post by disabled_20220313 on 2006-12-19
I think I know what your problem is.

You have to run the program that opens the file you want to have root permissions to write to.

ie.

If you run  ```
nano /etc/fstab
``` 
The nano program is run using user priviledges, and so thats how the fstab file is opened. Fstab is only opened with user privileges hence you cannot edit it.

Compared to ```
 sudo nano /etc/fstab
``` 
Now nano is running as root, and so can open *and* edit the fstab file.

Hope this helps.

---

### Post by raul_ on 2006-12-19
Or you can run
```

sudo nautilus

```

And navigate in root mode

---

