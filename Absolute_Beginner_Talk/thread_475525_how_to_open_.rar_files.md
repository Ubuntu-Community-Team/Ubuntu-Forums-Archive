---
title: "how to open .rar files"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-16
How do i open .rar files

---

### Post by Golyadkin on 2007-06-16
Run this command:
> 
sudo apt-get install rar

then you can use the Archive Manager that comes with Ubuntu.

---

### Post by ajmannen on 2007-06-16
When i try to extrack something it says that jscript is not installed right

---

### Post by Golyadkin on 2007-06-16
Strange. JavaScript doesn't have anything to do with extracting rar files as far as I know. 
What are you trying to extract, and how do you do it?

---

### Post by llamakc on 2007-06-16
> **Golyadkin said:**
> Run this command:

then you can use the Archive Manager that comes with Ubuntu.

This is the archiver. The extractor is a separate package.

```

sudo apt-get install unrar

```

```

unrar e nameof.rar

```

to extract to the current directory.

---

### Post by Golyadkin on 2007-06-16
Ah yeah, I missed that one. Am still sleepy :) I meant to write
> 
sudo apt-get install rar unrar


But still, would that explain a Javascript error?

---

### Post by llamakc on 2007-06-16
You're right: the OP needs to provide more information. Either by cut/pasting the error or providing a screenshot.

I wouldn't be surprised if the archive has some sort of installer (or script) and the OP is running that before extracting it, or the error is a separate and new error after a successful extraction.

---

