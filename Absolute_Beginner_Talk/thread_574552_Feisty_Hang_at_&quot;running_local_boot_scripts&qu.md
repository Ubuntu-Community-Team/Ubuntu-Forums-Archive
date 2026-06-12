---
title: "Feisty Hang at &quot;running local boot scripts&quot;"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by nrfool on 2007-10-12
Hi, guys,
My ubuntu feisty got stuck at the step "running local boot scripts". I did some search, and it seems that people were able to skip this step (when feisty gets stuck there) by hitting "enter" key or "ctrl+c" and eventually they get a root promot. Unfortuantely, that don't work for me. I can't get a shell to type any command. The only thing I can do is to "alt+print screen+REISUB".
Any help will be greatly appreciated!

---

### Post by A Whale Of A Time on 2007-10-13
I'm having the same problem.

---

### Post by flubio123 on 2007-10-14
I am also having this problem.

---

### Post by flubio123 on 2007-10-14
[http://ubuntuforums.org/showthread.php?t=563693&highlight=hang+at+local+boot+scripts](http://ubuntuforums.org/showthread.php?t=563693&highlight=hang+at+local+boot+scripts)

---

### Post by nrfool on 2007-10-14
Thanks for the link. But the link essentially suggests to hit "enter" that should give me a promote. Unfortuantely, this doesn't work for me. When I hit enter, the cursor just jumps one line, and no promote comes out.

---

### Post by Krapiva on 2007-10-16
try ALT+F2 to change

then u can return to ALT+F1 (for me it's blinking white...wrong video settings?)

i got this error after rebuilding kernel

---

### Post by icohen on 2007-10-21
I am having this same problem in Gutsy. Startup hangs at 

[INDENT]Running local boot scripts (/etc/rc.local) [OK] [/INDENT]

Anything I type (ctrl-c alt-f2, enter) just prints to the screen and moves the cursor down a line.

---

### Post by icohen on 2007-10-21
It's fixed! Alt-F2 did in fact bring me to a login prompt. Perhaps I wasn't using the Fn key on my macbook before. After logging in, I replaced my xorg.conf with a backup copy and restarted with the command
```
sudo /etc/init.d/gdm restart 
```

---

