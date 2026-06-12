---
title: "Update or add to $PATH Edgy"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by stchman on 2007-03-09
Hello I have a question if I type:

echo $PATH it shows all the programs I can access in the PATH.  How to I add to this path as I added the JAVA 2 SDK and don't want to type out the complete path for javac?  I thought it was in like a .profile somewhere.

Thanks.

---

### Post by taurus on 2007-03-09
You would add it to your ~/.bashrc.

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Add these two lines to it.

```
PATH=$PATH:/path_to_new_directory
export PATH
```

---

### Post by stchman on 2007-03-10
> **taurus said:**
> You would add it to your ~/.bashrc.

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Add these two lines to it.

```
PATH=$PATH:/path_to_new_directory
export PATH
```

I guess then I need to restart the workspace.

---

### Post by taurus on 2007-03-10
Either log out and back in or run this command from a terminal.

```
source ~/.bashrc
```

---

### Post by stchman on 2007-03-10
> **taurus said:**
> Either log out and back in or run this command from a terminal.

```
source ~/.bashrc
```

That worked, you rule.

Thanks.

I don't know what I would do without this forum.

Now if I can just get my Atheros 5006EG wireless card in my laptop to work that would be awesome.

---

