---
title: "Beryl no longer working after enable desktop effects"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by nb123 on 2007-09-13
I recently installed beryl effects and they were working fine, until I selected desktop effects and was notified that they could not be enabled, but then when I tried to launch beryl after restarting my computer, it wouldn't work. I searched around and someone said type 'beryl' in the terminal, and this worked for a bit, but then when I exited the terminal the title bars of my application windows had disappeared!? 

How do I disable desktop effects, I'm more than happy with beryl!

Also, while I'm at it, I'm trying to transfer my firefox profile from windows xp to ubuntu, and I read up on how to do it but after copying the folder to my ubuntu 'firefox' folder, and editing the profile.ini by changing the 'path=' and isrelative=0, what it does is create another 'profile.ini~' and when I launch firefox it simply creates a new profile folder... how do I get around this?

---

### Post by startherepodcast on 2007-09-13
Thats because desktop Effects is using Compiz, which is a bit like Beryl and basically does the same. Try going to Synaptic Package Manager (System -> Administration) and Searching for compiz. Then remove all packages which are installed and try to enable Beryl again!

---

### Post by luisromangz on 2007-09-13
Well Compiz Fusion is better and has newer features, you shouldn't stick to Beryl.

That said, Beryl closing when you close the terminal window is normal beheaviour. When you launch a program from a terminal, if you don't specify that you want the new process to run without the terminal being it's parent process, the new process became a terminal's process child process. When you close the terminal, all its child process are killed.

If you don't want this behaviour, you should append & to the command you want to launch.

In this case

```
beryl &
```

Bye!

---

