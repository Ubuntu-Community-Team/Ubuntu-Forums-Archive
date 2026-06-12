---
title: "Launcher problems"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-04-28
I've noticed that for some reason I can't make launchers for some things (Namely - Frets on Fire that is installed to my home directory, and Open Arena, which is also installed in my home directory...

If I right-click and create a launcher of the type Application, and browse to the file '/home/<my_home_folder>/FretsOnFire/fretsonfire' my launcher appears as it should. But clicking on it does absolutely nothing.

I have tried setting permissions on the launcher its self to allow execution, that didn't work. I have also tried a Launcher of the type File, and no go there either.

For some reason it seams as if the executable 'fretsonfire' will only run if opened from my home folder???

Any help would be appreciated!

---

### Post by Metacarpal on 2007-04-28
Try this: right-click your launcher and choose Properties or Edit (can't remember what it's marked as, and I'm not on my Ubuntu box so I can't check).  In the command section, make this change:

If the command is listed as: 

```
/home/*username*/fretsonfire/fretsonfire
```

change it to:

```
cd /home/*username*/fretsonfire; ./fretsonfire
```

Some programs need to be run from within their own directory so they can find some of their files.

---

### Post by jondecker76 on 2007-04-29
Thanks a lot, thats exactly what I was looking for!

---

### Post by Metacarpal on 2007-04-29
Glad I could help! :)

---

### Post by jondecker76 on 2007-05-06
Finally got around to trying this

However it didn't work.. 

Any more suggestions?

---

### Post by jondecker76 on 2007-05-12
bump

---

### Post by Happy_Man on 2007-05-12
I believe that the command was posted wrong, it should be 
```
cd /home/*username*/fretsonfire ./fretsonfire
```

---

### Post by jondecker76 on 2007-05-12
Tried that too - here is the error message i get:

Details: Failed to execute child process "cd" (No such file or directory)

---

