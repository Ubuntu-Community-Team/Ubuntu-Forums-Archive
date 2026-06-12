---
title: "How to write a script to change directories"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Harvs on 2007-03-23
Hi

I'm new to Ubuntu - and think it is excellent. I'm stating to have a look at programing, and Python. I've been saving my python scripts to a dedicated directory. When I open I new terminal, I find it a pain to navigate to my python directory every time, so thought I'd write a script to change directories and save this in my home directory, so I can just run the script and it will take me straight there.

Here's the script:

```
#!/bin/bash
cd /home/files/"Harvey's Folder"/ubuntu
```

I've saved this in my home directory and called it "go".

When I try to run it, using,

```
./go
```

nothing happens! What am I doing wrong?!

---

### Post by paper0k on 2007-03-23
Try this
```
source go
```;)

---

### Post by Harvs on 2007-03-23
Fantastic - thanks!

---

