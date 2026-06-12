---
title: "unix command to show progress?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by pantsroptional on 2007-03-07
Sometimes I will use 'cp' or 'mv' to copy/move one big file and other times I rearrange my drives which will be moving gigs of stuff which can take several minutes (or longer) to return back to the prompt. 

Is there some unix command I can use or something that can give me an idea of the status so that I know that things are actually happening and nothing is getting hung up? I know I can use gnome but sometimes this will be with scripts and I'd really much rather use the command. It's nice to just 'sudo' and not have to worry about file permissions for a command where in the file explorer in Ubuntu there is no "administrator mode" like there is in KDE menus.

Any suggestions?

---

### Post by chili555 on 2007-03-07
From man mv:```
 -v, --verbose
              explain what is being done
```

I don't know if this will give you enough information, but it's worth a try.

---

### Post by jkeyes0 on 2007-03-07
If you're looking for an "Administrator mode" for gnome (nautilus) you can use the following command:

```
gksudo nautilus
```

---

