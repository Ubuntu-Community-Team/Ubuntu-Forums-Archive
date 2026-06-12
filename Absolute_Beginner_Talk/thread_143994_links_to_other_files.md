---
title: "links to other files"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-13
I have opened a directoy /var/lb/mixmaster/mix where the fliles are written in red with a black filter over them linking them to another directory, If I try to open mix.cfg with emacs and save the file it gives the comand not such file or directory

mix.cfg - >/etc/mixmaster/rem.conf
update.conf - >/etc/mixmaster/update.conf


lex1;) ;)

---

### Post by Pragmatist on 2006-03-15
They are broken links.  A broken link happens like this.  I have FILE and I want to make a symbolic link to FILE.  So, I do this:
```
ln -s /path/to/FILE FILE_LINK
```  Now if I do a long listing of the directory where FILE_LINK is I get this:

FILE_LINK --> /path/to/FILE

Now, if you remove FILE or move it to another location, FILE_LINK will be pointing to something that either doesn't exist, or is at a different location.

Do this and wait until it finishes:
```
updatedb
```

Then do this:
```
locate rem.conf
```
And this:
```
locate update.conf
```

If you get alot of hits when you try and locate those files, you can filter your results using **grep** for instance:
```
locate rem.conf | grep mix
```
 And this:
 ```
locate update.conf | grep mix
```

---

