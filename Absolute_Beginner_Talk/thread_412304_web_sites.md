---
title: "web sites"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by papum on 2007-04-17
Hi, Im new to linux for about a week , i ve learned alot from reading but cant get a website to be seen other than as files. Ive seen several threads about it  and tried them but it doesnt work. My domain name works great but all you see is the files I put in /var/www folder. Is something other than php needed to work?

Thanks in advance

---

### Post by bobplano on 2007-04-17
when you click on them what happens?

---

### Post by papum on 2007-04-17
the index file will pop up as a webpage the others in folder will open according to what format they are.

---

### Post by bobplano on 2007-04-17
are you saying it has index of / at the top then lists the files, and when you click on them then they open into a page like this?

---

### Post by papum on 2007-04-17
exactly

---

### Post by bobplano on 2007-04-17
all you need to do then is name a file index.php or index.htm(l). the webserver doesn't know which file to show first otherwise

---

### Post by papum on 2007-04-17
check it out [http://www.childsplay.homeftp.net/](http://www.childsplay.homeftp.net/)

---

### Post by bobplano on 2007-04-17
you need to edit the httpd file where it says 
```
<IfModule dir_module>
    DirectoryIndex
</IfModule>

```

and change it to something like

```
<IfModule dir_module>
    DirectoryIndex index.php index.html index.html.var index.htm
</IfModule>

```

---

### Post by papum on 2007-04-17
i changed the index file extension to php and it worked. doex that mean i could only use php, not htm(l)?  If so, I really appreciate your time in helping me. Much thanks!

---

### Post by bobplano on 2007-04-17
if you add multiple ones like mine it just goes down the list if it can't find one. so if you want html to show first put it first

---

### Post by papum on 2007-04-17
thats what i was, there was no .htm in that line. Another question , how do change the directory to work out of public_html in home instead having to go through root all the time?

---

### Post by heimo on 2007-04-17
> **papum said:**
> thats what i was, there was no .htm in that line. Another question , how do change the directory to work out of public_html in home instead having to go through root all the time?

Personally, I prefer to handle this by using file permissions / groups. Make yourself and www-directory a member of www-data group and give it write+read permission. This thread may be helpful:
[http://ubuntuforums.org/showthread.php?t=25389](http://ubuntuforums.org/showthread.php?t=25389)

---

