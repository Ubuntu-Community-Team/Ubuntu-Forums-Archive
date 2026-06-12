---
title: "ls command - going line by line"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by SirGrant on 2007-04-25
Hey my dad taught me how to do this about a month ago but I forgot how.  Lets say I use the ls command on a folder with 1000 files in it.  Straight up it will just list all the files and take me straight to the bottom of the list.  How do I do it so it does it like one page at a time so like it shows me 20 files and then I think I have to hit ctrl-n to get the next 20.  I tried doing man ls but it was too beyond me so I couldn't figure it out.  Thanks for the help.  Oh also what are the commands to scroll up and down when you do this too.

---

### Post by Cypher on 2007-04-25
If you just want to go forward then
```

ls -l | more

```
If you want to back and forth using the arrows or page-up/down
```

ls -l | less

```

---

### Post by taurus on 2007-04-25
```
ls -la | more
```
Hit the space bar for the next 24 lines.

---

### Post by SirGrant on 2007-04-25
thanks guys problem solved!

---

