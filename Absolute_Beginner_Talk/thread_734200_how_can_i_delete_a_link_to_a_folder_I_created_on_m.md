---
title: "how can i delete a link to a folder I created on my desktop?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-03-24
Hi all :),
          I created a link on my desktop but i cant delete it. Whenever i try it says:

Error: Not on the same file system "Link to Ubuntu Applications" while deleting

I also tried:

```

rmdir "Link to Ubuntu Applications"

```

in the terminal but it says:

"No such file or directory"

Can someone help please?

Thanks :D

Regards

Q

---

### Post by xeth_delta on 2008-03-24
Open a terminal and go to "~/Desktop". List the contents:
```
ls
```
To remove a link, simply type
```
rm link_name
```
If the link name contains spaces, these should pe preceded by "\", for example:
```
rm link\ to\ a\ file
```

---

### Post by quddusaliquddus on 2008-03-24
thanks !! :D

---

### Post by Oldsoldier2003 on 2008-03-24
> **xeth_delta said:**
> Open a terminal and go to "~/Desktop". List the contents:
```
ls
```
To remove a link, simply type
```
rm link_name
```
If the link name contains spaces, these should pe preceded by "\", for example:
```
rm link\ to\ a\ file
```

That is exactly why conventional Linux wisdom says, "Never use spaces in file or directory names. Ase an underscore instead."

---

### Post by Tyke91 on 2008-03-24
> **Oldsoldier2003 said:**
> That is exactly why conventional Linux wisdom says, "Never use spaces in file or directory names. Ase an underscore instead."

in fact, capitalization is more trouble than it's really worth in the long run:)

---

### Post by Oldsoldier2003 on 2008-03-24
> **Tyke91 said:**
> in fact, capitalization is more trouble than it's really worth in the long run:)

yeah like the stupid ~Desktop and ~.Trash folders...

---

### Post by xeth_delta on 2008-03-24
Hmm, I guess this too is a matter of preference. Capitalization does not bother me, on the contrary. :) Nevertheless, I agree about names with spaces, sometimes it can be annoying, but given that in a command line space can separate arguments in commands, the "\" is necessary.

---

