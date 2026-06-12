---
title: "Find files and open them with gimp"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by GreenLantern33 on 2008-03-26
I've been playing around with working from the command line.

Here is an idea I had....  Find my biggest picture files and open them with gimp so that I could then resize them if I wanted.

I was trying something like this:
[FONT=Tahoma][SIZE=2]find ~/pictures -name [/SIZE][/FONT][FONT=Tahoma][SIZE=2]"*.jpg"-size +2000k | gimp

That, of course, doesn't work.  How would I do something like this?

Also, how do I limit it to say.... 5 results.  I don't want gimp to open 50 files at a time.

Thanks!
[/SIZE][/FONT]**[FONT=Verdana, Arial, Helvetica, sans-serif][/FONT]**

---

### Post by kpkeerthi on 2008-03-26
```
find ~/pictures -name "*.jpg"-size +2000k **-exec** gimp
```

---

### Post by GreenLantern33 on 2008-03-26
find: missing argument to '-exec'

---

### Post by kpkeerthi on 2008-03-26
```
find ~/pictures -name "*.jpg"-size +2000k -exec gimp '{}' ';'
```

---

### Post by GreenLantern33 on 2008-03-26
Ok, I found this before I read yours.  What is the difference?
```
find ~/pics -name "*.jpg" -size +2000K -exec gimp '{}' \;
```

Anyway, that will only open one file.  I want to open all the files that the search finds at the same time.  Any ideas?

---

### Post by kpkeerthi on 2008-03-26
';' and \; both marks the end of the command

Try this to fork gimp to the background.
```
find ~/pictures -name "*.jpg" -size +2000k -exec gimp '{}' **&** ';'
```

* I'm not in front of my linux box so I'm typing these from what I could recollect.

---

### Post by GreenLantern33 on 2008-03-26
Didn't work. :(

find: missing argument to '-exec'
bash: ;: command not found
[1]+ Exit 1

---

### Post by kpkeerthi on 2008-03-26
```
find ~/pictures -name "*.jpg" -size +2000k -print0 | xargs -0 gimp
```

---

### Post by kpkeerthi on 2008-03-26
The above command launches gimp once with all the paths found by the find command. -exec, however, cause gimp to launch once for each file found by the find command.

---

### Post by vanadium on 2008-03-26
Use "gimp-remote" instead to have all files loaded in the running instance of gimp.

---

### Post by GreenLantern33 on 2008-03-26
Ok, so I am running this:
```
find . -name "*foo*" | xargs -0 gimp-remote
```Gimp opens, everything is looking good, then I get an error that looks like this:
```
Opening '/home/user/pictures/./the_foo.jpg
' failed:

No such file or directory
```See that extra "./" in there?  How do I get rid of that?

By the way thanks for all your help on this.  This is why I love Linux.  Everything thing is possible, and everyone is willing to help.

---

### Post by GreenLantern33 on 2008-03-26
Ok I got it.  If I go back to using -exec everything works fine.
```
find . -name "*foo*" -exec gimp-remote "{}" \;
```

Now, how can I limit it so that it will open 5 files at a time?

---

### Post by kpkeerthi on 2008-03-26
> **GreenLantern33 said:**
> Ok, so I am running this:
```
find . -name "*foo*" | xargs -0 gimp-remote
```Gimp opens, everything is looking good, then I get an error that looks like this:
```
Opening '/home/user/pictures/./the_foo.jpg
' failed:

No such file or directory
```See that extra "./" in there?  How do I get rid of that?

By the way thanks for all your help on this.  This is why I love Linux.  Everything thing is possible, and everyone is willing to help.
./ is valid in that path. it just refers to the pictures directory. 
Does **/home/user/pictures/the_foo.jpg** exist?  (no ./ here)
What happens when you run
```
find . -name "*foo*" **-print0** | xargs -0 gimp-remote
```

---

### Post by markjensen on 2008-03-26
As an alternative to using GIMP, if you know what you want to do for resizing (setting a certain maximum resolution, or changing the jpeg compression), then a better choice would almost certainly be imagemagick.

---

### Post by GreenLantern33 on 2008-03-26
kpkeerthi:
See my second post, I got it.  Now I just need to limit it to five files.

Markjensen:
I might want to change the levels, crop it, rotate, etc.  That is why I wanted to use Gimp.

---

