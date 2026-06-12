---
title: "running a shell script"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by drorl on 2006-10-25
hi.
i wrote a short shell script to start few applicatons.
i changed its permissions so it will be excutable, but when trying to run it it says:"bash: ok: command not found".](*,) 
here are the file permissions:
-rwxr-xr-x 1 drorl drorl   33 2006-10-25 23:28 ok

what should i do?:-k 
thanks
dror

---

### Post by aysiu on 2006-10-25
Have you tried this? ```
./ok
``` Or are you just typing ```
ok
```?

---

### Post by bodhi.zazen on 2006-10-25
you can always copy ok to your path:```
sudo cp ok /usr/bin/ok
```

Edit: #-o thanks aysiu.

---

### Post by drorl on 2006-10-25
thanks.
it works for ./ok.
the question is what is the differnce?

---

### Post by TheMono on 2006-10-25
Just to clarify, the command 
```
ok
```

Will execute script 'ok' if it is in the /usr/bin directory (or some others...)

Whereas, 
```
./ok
```

Will execute script 'ok' within the current directory

---

### Post by aysiu on 2006-10-25
> **bodhi.zazen said:**
> you can always copy ok to your path:```
cp ok /usr/bin/ok
```
Shouldn't that be...? ```
sudo cp ok /usr/bin/ok
```

---

### Post by Paul133 on 2006-10-25
Aysiu, is the difference between needing sudo cp or just cp due to the write permissions of the file?

---

### Post by po0f on 2006-10-25
Paul133,

If just anybody could write to /usr/bin, they could easily replace a system binary with a virus.

---

### Post by aysiu on 2006-10-25
> **Paul133 said:**
> Aysiu, is the difference between needing sudo cp or just cp due to the write permissions of the file?
It's not the permissions of *ok*. It's the permissions of */usr/bin*.

---

### Post by d3v1ant_0n3 on 2006-12-03
I love the search function on this forum! It works! Another problem solved for me:D

---

### Post by MGStreak on 2007-06-10
> **d3v1ant_0n3 said:**
> I love the search function on this forum! It works! Another problem solved for me:D
I would just like to post an 'AMEN!' to this line.

And a thank you to those in this thread who showed me how to solve this problem!

---

### Post by Nikron on 2007-06-10
What I do is create /home/user/bin/ , and include that into my path so I don't mess with /usr/bin/

---

