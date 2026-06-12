---
title: "Opening RAR Files"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by KamenRiderNecro on 2008-03-29
Hello, folks!

I am totally new at this Ubuntu thing, so humor me please...

I've DL'd several .rar files and also added 7zip to my program list. Problem is, I can't find 7zip on my system even after restarting my machine after DLing/installing it. And it refuses to come up when I try to open the files. Help?

---

### Post by smoker on 2008-03-29
just a suggestion, try ctrl+f2, and typing in 'gksudo 7zip' without the quotes. it may work!

NO, doesn't work, sad to say!

---

### Post by kane77 on 2008-03-29
> **KamenRiderNecro said:**
> Hello, folks!

I am totally new at this Ubuntu thing, so humor me please...

I've DL'd several .rar files and also added 7zip to my program list. Problem is, I can't find 7zip on my system even after restarting my machine after DLing/installing it. And it refuses to come up when I try to open the files. Help?

You don't need 7zip to open rar files, you just have to install the unrar-nonfree package. You do that by searching and installing that package in Synaptic or opening terminal and typing ```
sudo aptitude install unrar-nonfree
```

then the default archive manager will open rar files with no problems.

---

### Post by mali2297 on 2008-03-29
I think that the package is just called **unrar**. Make sure that you have the **multiverse** repository enabled (through **Settings -> Repositories** in Synaptic).

---

### Post by T2manner on 2008-03-29
you could just go to ADD/REMOVE and it's an app.

---

