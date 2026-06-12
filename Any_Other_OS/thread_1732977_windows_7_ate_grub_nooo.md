---
title: "windows 7 ate grub nooo"
date: 2011-04-18
forum: Any Other OS
---

### Post by bbowerman on 2011-04-18
OK so I was running Debian, and then reinstalled windows 7, and it removed grub, I have a disc I am booted into Debian right now but have to use a CD to boot every time, how can I get grub back. all help appreciated thanks.:confused:

---

### Post by mikewhatever on 2011-04-18
You have to reinstall Grub. What version of Debian do you have?
...and by the way, W7 can't eat Grub, in fact, it can't even read ext* file systems by default.

---

### Post by bbowerman on 2011-04-18
6.0 squeeze i tried using aptitude remove Grub, then using aptitude install grub.

---

### Post by overdrank on 2011-04-18
Moved to Other OS/Distro Talk

---

### Post by bbowerman on 2011-04-18
huh?

---

### Post by bbowerman on 2011-04-18
and I know it cant eat grub it just sounded kind of funny haha

---

### Post by HunkirDowne on 2011-04-18
> **bbowerman said:**
> 6.0 squeeze i tried using aptitude remove Grub, then using aptitude install grub.

You might try:
```

# aptitude install --reinstall grub

```

If that doesn't work you might hack the packages list with dpkg and your favorite editor.

```

# dpkg --get-selections | tee ~/dpkg-get-selections.list
# cp -ip ~/dpkg-get-selections.list ~/dpkg-set-selections.list
# vim ~/dpkg-set-selections.list

```

Whilst in editor (vim here, or use nano), search for deinstall and you should find grub rather quickly.

```

# dpkg --clear-selections
# cat ~/dpkg-set-selections.list | dpkg --set-selections
# aptitude update
# aptitude install --reinstall grub
# update-grub

```

---

