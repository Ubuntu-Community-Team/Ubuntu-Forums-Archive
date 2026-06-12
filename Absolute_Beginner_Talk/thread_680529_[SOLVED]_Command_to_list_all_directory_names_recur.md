---
title: "[SOLVED] Command to list all directory names recursively?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by kpkeerthi on 2008-01-28
```
ls -lR
``` prints all folders and sub-folders including the files. But I need a command that prints only the folder names including the names of the sub-folders, recursively. So I tried ```
ls -lRd
``` but it prints nothing. Any ideas why?

Strangely enough ```
ls -ld
``` prints the names of all the folders in the current directory.

---

### Post by LaRoza on 2008-01-28
```

sudo aptitude install tree

```

```

tree

```

---

### Post by kpkeerthi on 2008-01-28
Whoa... Thanks LaRoza. 
```
tree dR
``` did the trick.

It was ```
sudo pacman -S tree
``` for me :)

---

### Post by bodhi.zazen on 2008-01-28
to list directories from your current :

```
ls -d */
```


Or use find

```
find . /* -type d -maxdepth 0
```

alternate, 

```
ls -F / | grep /
```

NOTE: the / in that last grep searches on "/" which is added to directories by the -F flag

---

### Post by kpkeerthi on 2008-01-28
Thanks. Would you mind explaining what does ```
*/'
``` denote in ```
ls -d */'
```?

Edit: Just noticed it has been corrected to ```
*/
``` in your post. Make sense now. Thanks.

---

### Post by LaRoza on 2008-01-28
> **kpkeerthi said:**
> Whoa... Thanks LaRoza. 
```
tree dR
``` did the trick.

It was ```
sudo pacman -S tree
``` for me :)

No problem, sorry about the command aptitude though.

---

### Post by LaRoza on 2008-01-28
<edit>

---

### Post by bodhi.zazen on 2008-01-28
actually it is idiosyncratic syntax to ls :twisted:

ls -d */  lists the directories in your current directory. It does not accept the -R flag :(

Try it out :

ls -d
ls -d *
ls -d */
ls -dR */

---

