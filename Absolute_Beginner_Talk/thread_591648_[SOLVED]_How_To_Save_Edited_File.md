---
title: "[SOLVED] How To Save Edited File?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by snerd on 2007-10-25
So I've installed MoBlock and I need to edit a couple of files. When I add the new lines and then try to save it I get an error that I don't have permission.

Thanks!

---

### Post by taurus on 2007-10-25
You need to run the command with either sudo or gksudo in front since you are editing system files and only root can do that.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
gksudo gedit **filename**
```

---

### Post by Maestro23 on 2007-10-25
> **snerd said:**
> So I've installed MoBlock and I need to edit a couple of files. When I add the new lines and then try to save it I get an error that I don't have permission.

Thanks!

Need **sudo** or** gksudo** in front of your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snerd on 2007-10-25
Got it, thanks! Definitely different than winbloze, but I deleted that system and so I'm having to learn this one.

---

### Post by Maestro23 on 2007-10-25
> **snerd said:**
> Got it, thanks! Definitely different than winbloze, but I deleted that system and so I'm having to learn this one.

No prob man.  Welcome to Ubuntu.

Please mark this thread SOLVED using Thread Tools.

Thanks.:)

---

