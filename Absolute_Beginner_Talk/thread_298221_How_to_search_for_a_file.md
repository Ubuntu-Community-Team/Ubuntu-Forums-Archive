---
title: "How to search for a file"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-11-12
I know this seems a simple question but how do you search for a file or folder. For example, I've installed wine with Automatix2, I see it in Synapic package manager but where is wine and winetools in my system. Using File Browser-

Places>Home Folder>File System and searching for "wine" or "winetools" brings no result, nothing appears.

What's happening, what have I missed out?

---

### Post by bodhi.zazen on 2006-11-12
> **Handssolow said:**
> I know this seems a simple question but how do you search for a file or folder. For example, I've installed wine with Automatix2, I see it in Synapic package manager but where is wine and winetools in my system. Using File Browser-

Places>Home Folder>File System and searching for "wine" or "winetools" brings no result, nothing appears.

What's happening, what have I missed out?

```
which wine
whereis wine
locate wine
```

You wine configuration files are in ~/.wine. "dot" files are hidden.

---

### Post by bruenig on 2006-11-12
most applications are in /usr/bin/
so wine is likely at /usr/bin/wine.

---

### Post by Handssolow on 2006-11-12
Thanks for your help, I've found wine but why didn't my search function find it using the File Browser?

---

### Post by bodhi.zazen on 2006-11-12
> **Handssolow said:**
> Thanks for your help, I've found wine but why didn't my search function find it using the File Browser?

GUI are not perfect. Just one more reason to learn a little about the CLI.

---

