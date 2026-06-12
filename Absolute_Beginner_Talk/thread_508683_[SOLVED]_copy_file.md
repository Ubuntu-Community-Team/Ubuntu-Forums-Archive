---
title: "[SOLVED] copy file"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-07-24
I need to copy and executable file from a folder on my desktop to my /usr/local/bin

can anyone tell me how to do this?

---

### Post by Cypher on 2007-07-24
```

sudo cp ~/Desktop/<file name> /usr/local/bin

```
If you want to do it within the GUI entirely, then hit ALT-F2 and type
```

gksu nautilus

```
Now browse to the Desktop folder, CTRL-C the file you want to copy, browse over to /usr/local/bin and CTRL-V to paste. Remember to exit this File Manager once you're done with this task.

---

### Post by pizzutz on 2007-07-24
sudo cp ~/Desktop/<file.name> /usr/local/bin

---

### Post by tomcheng76 on 2007-07-24
sudo cp ~/Desktop/filename /usr/local/bin

---

### Post by jrandolph on 2007-07-24
Thank you all for your prompt reply
This worked great

---

