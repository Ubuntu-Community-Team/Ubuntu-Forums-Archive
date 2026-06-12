---
title: "deleting file from desktop"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-09-30
I have tried several ways to install realplayer and finally got it. However, I have a file left on my desktop from helix I think and I can not move it or delete it. When I do try I get (you do not have permissions to change it or its parent folder). So what do I need to do to get this file off my desktop as it is no longer needed.
Thanks

---

### Post by bulldog on 2006-09-30
Use sudo rm -r package

---

### Post by davmac on 2006-09-30
Press alt-F2 and in the dialog box type "gksudo nautilus". Key in your password. You can then navigate to your desktop and should be able to delete the file.

Hope this helps,

Dave Mac

---

### Post by aysiu on 2006-09-30
Alt-F2 ```
gksudo nautilus
``` and then delete it.

If you're using Kubuntu, the command after Alt-F2 is *kdesu konqueror*. If you're using Xubuntu, it's *gksudo thunar*.

I would avoid using the terminal command *sudo rm -r* under any circumstances. Accidentally typing the wrong thing after that command can remove your entire filesystem!

---

### Post by Tucatts on 2006-09-30
Thanks! worked like a charm and most importantly I know how to correct this from now on.

---

