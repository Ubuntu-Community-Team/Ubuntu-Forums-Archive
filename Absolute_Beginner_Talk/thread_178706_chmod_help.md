---
title: "chmod help"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Tortanick on 2006-05-18
Is there some way to do a recursive chmod that only affects folders and not files.

---

### Post by frodon on 2006-05-18
Yes, this should do the job : ```
sudo chmod 755 `find /path -type d`
```This command will change the rights to 755 to all directories the recursive way from the path you put instead of **/path**.

Tell me if it works, i didn't tried it myself but it should work.

---

### Post by Tortanick on 2006-05-18
dosn't work, it says no such file or directory, I think its trying to change permissions for find

---

### Post by steve.horsley on 2006-05-18
Did you copy-and-paste? 
Those are backticks (just left of the digit 1 on my UK layout keyboard).

---

### Post by Tortanick on 2006-05-18
changed it to backticks it now says 

```
find: invalid argument `-d' to `-type'
chmod: too few arguments
```

---

### Post by frodon on 2006-05-19
Ok so try it like that : ```
sudo find /path -type d -exec chmod -v 755 {} \;
```

---

### Post by Tortanick on 2006-05-19
works fine :)

---

### Post by Arndt on 2006-05-19
[QUOTE=frodon]Ok so try it like that : ```
sudo find /path -type d -exec chmod -v 755 {} \;
```[/QUOTE]

If the command within backticks is likely to generate a lot of filenames, it may be good to use 'xargs':

```
find /path -type d | xargs chmod -v 755
```

'xargs' takes a whole chunk of names at a time, so that 'chmod' does not get called so many times.

---

### Post by Tortanick on 2006-05-19
frade xrags isn't as reliable, for example if you want to chmod to 444, then it locks itself out and can't change subdirectories, even with sudo.

---

### Post by vordude on 2008-02-19
> sudo find /path -type d -exec chmod -v 755 {} \;


I just need to be clear   

Essentially The "/path" in that line is the path where you start chmoding directories recursively??


So do I need to 


```
sudo find /var/www -type d -exec chmod -vR 755 {} \;
```


do chmod directories inside of and including /var/www

what's the deal with the backslash on the end?

---

