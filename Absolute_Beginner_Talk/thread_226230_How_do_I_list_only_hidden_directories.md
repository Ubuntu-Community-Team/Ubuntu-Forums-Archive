---
title: "How do I list only hidden directories?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-07-31
How do I list only hidden directories?  No directories, no files, no hidden files.

---

### Post by [S|G] on 2006-07-31
I still haven't figured out how not to show normal directories, but to show directories only, try this:
```

ls -lap|grep /

```

---

### Post by croak77 on 2006-07-31
> **tux101 said:**
> How do I list only hidden directories?  No directories, no files, no hidden files.

```
find -maxdepth 1 -type d -name ".*"
```

That's for all directories in the current directory. If you want to search recursively just remove '-maxdepth 1' or edit the numerical value to however deep you want.

---

### Post by tux101 on 2006-08-01
> **'[S|G] said:**
> I still haven't figured out how not to show normal directories, but to show directories only, try this:
```

ls -lap|grep /

```

Is there a way I can make it list both vertically and horizontally?  Just like the "ls" does.  This way I do not have to scroll too much.

---

### Post by nalmeth on 2006-08-01
ls -a

---

### Post by verbatim210 on 2006-08-01
remember is msdos how u typed **dir /p** 
how do we do that in bash?

this function lists in pages and you press any key to go to the next page.  this is useful for browsing folders with massive content.

---

### Post by fakie_flip on 2006-08-01
> **verbatim210 said:**
> remember is msdos how u typed **dir /p** 
how do we do that in bash?

this function lists in pages and you press any key to go to the next page.  this is useful for browsing folders with massive content.

ls | less

---

### Post by tux101 on 2006-08-01
> **nalmeth said:**
> ls -a

That shows everything.  Contradiction to the original post.

---

### Post by [S|G] on 2006-08-02
You could use
```

ls -lap|grep /|less

```
or
```

ls -lap|grep /|more

```

---

### Post by carlosqueso on 2006-08-02
```
ls -d .*/
``` seems to work.

---

### Post by fakie_flip on 2006-08-11
> **verbatim210 said:**
> remember is msdos how u typed **dir /p** 
how do we do that in bash?

this function lists in pages and you press any key to go to the next page.  this is useful for browsing folders with massive content.

another solution to your problem would be to use midnight commander. i believe it is in the universe or multiverse repositories, so you will have to enable them first if you have not already and then do this.

```
sudo apt-get install mc
```

if you would like to read about it, then do this.

```
apt-cache show mc
```

---

