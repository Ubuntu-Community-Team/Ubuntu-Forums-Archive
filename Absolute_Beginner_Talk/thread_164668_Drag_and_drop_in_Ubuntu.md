---
title: "Drag and drop in Ubuntu"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Mrtn on 2006-04-23
I have a question, is there anyway so you can drag and drop files in linux? Everytime I try to do it, it says I do not have the permissions. Is there any other way to do it than logging in via root?

Sometimes I want to extract or copy something, and I wonder what is the easiest way to do it. I hope there is some kind of terminal command I can type in so I can temporarily do my unsafe stuff and then jump back to my non-root account 

I have checked the ubuntu 5.04 guide and did not find any explanation =/

---

### Post by mostwanted on 2006-04-23
You can drag and drop wherever you have permission. The reason you're getting error messages is because you're trying to write something to somewhere outside your home folder.

Please don't log in as root, you're ruining the elegant way Ubuntu works:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

If you want to drag and drop files in Nautilus, open it with sudo nautilus. If you want to make this easier you can create a launcher that executes the command

```
gksudo nautilus
```

---

### Post by Mrtn on 2006-04-23
I know I am not doing it the right way, hence I posted the thread =)

Thanks for your help, I'll do it that way!

It worked! YAY! /me remembers and bookmarks thread just in case

If I close the window then everything is fine again?

---

### Post by Mrtn on 2006-04-23
I have another problem, maybe someone can help me?

My computer keeps on crashing because it reaches a temperature which is too high. Before ubuntu I used windows and it didn't crash.

I think there are multiple explanations possible: 

- The fan speed is altered by ubuntu which causes the PC to reach a too high temperature and crash.

- The computer was also overheating in windows but it did not shut down because it doesn't have a safety built in like ubuntu. How do I remove the safety?

So anybody know how I can fix this problem? Thanks!

---

