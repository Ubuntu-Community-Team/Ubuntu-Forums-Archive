---
title: "I'd like to do Terminal things on files I select in the GUI"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-09-05
That's basically it... I think it would be great if we could do the following three things in Ubuntu:

1.  Right-click on a file (or group of files) and select "Terminal command" to bring up a mini terminal-like window that allows a Terminal command to be applied to the file(s).

2.  Be able to access protected directories / files / commands in Nautilus

3.  Right-click on a file and select "Open parent folder in a Terminal window" so Terminal commands could be performed on that file

My thinking here is that if I want to run a Terminal command on a file that's right in front of me on the Desktop, I should be able to quickly.  As it is now, you have to open a Terminal window, then text-navigate to the file manually, then perform the command or commands.

What do you think of these ideas, and does anybody know if there are ways to do this already?

Thanks for your input.

-Mark

---

### Post by Skogix on 2006-09-05
You should be able to do all that with scripts. Im checking it out tomorrow :P.

---

### Post by jd65pl on 2006-09-05
You can navigate to a file / folder in terminal by dragging and dropping for nautilus.

A root access nautilus can be launched by:

```
gksudo nautilus
```

---

### Post by Seq on 2006-09-05
You may wish to investigate the packages "nautilus-open-terminal" and "nautilus-actions" as well. The former provides an "Open in Terminal" context option on folders. The latter is essentially an easy way of doing some other actions (I have not really looked at that one that much).

---

### Post by mjpatey on 2006-09-05
jd65pl,

Thank you!  I didn't know of this functionality.  That's partly why I posted, hoping some of this was already possible.  This is extremely helpful to me, and yet another shining reason Ubuntu (and Linux in general) is so great.

-Mark

---

### Post by mjpatey on 2006-09-05
Thank you, Seq.  I'll check that out ASAP.  Sounds handy!

---

### Post by aktiwers on 2006-09-05
You can also just type the command you want to use, and then drag and drop the file into the terminal.

---

