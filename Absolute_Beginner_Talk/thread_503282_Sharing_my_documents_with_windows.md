---
title: "Sharing my documents with windows"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by simormate on 2007-07-17
I have read all the posts I found about this subject but I didn't found all the answers I had needed.

I have windows and ubuntu 7.04 on the same computer, and a third partition in ext3 for the documents and the /home folder. I would like to access and organize my documents from both operating systems.

For the moment I can do it from windows but not from Ubuntu. The problem is that if I move or create some files on this partition in windows, the owner of these files in Ubuntu will be "root", so I won't be able to move or modify them.

My questions are:
How to make this partition accessible and writeable from both operating systems?
How to keep a high level of security of my personal files at the same time?

I am a newbie, so I don't know a lot about Ubuntu.
Thanks,
Mate

---

### Post by luisromangz on 2007-07-17
You can always change the owner of that files using the chmod command.

```

sudo chmod <your user> <the file you want to own>

```

---

### Post by simormate on 2007-07-18
> **luisromangz said:**
> You can always change the owner of that files using the chmod command.

```

sudo chmod <your user> <the file you want to own>

```

I did this but it didn't work.
The program expects a "mode" and not a user name.
It seems to me that with chmod I can only change the rights and not the owner.

---

### Post by simormate on 2007-07-18
Ok I found the solution.
it wasn't chmod but chown command that I needed to use.

Another question I have now is what permissions are recommended for my documents? How should I set it to be sure that my personal stuff cannot be read? And do I need to set permissions for my media files if I want to share them in p2p applications?

Thanks,
Mate

---

