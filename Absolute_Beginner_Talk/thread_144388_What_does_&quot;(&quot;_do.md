---
title: "What does &quot;(&quot; do?"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by torx on 2006-03-14
i was wondering if anyone could tell me what does entering the command "(" in console does??

---

### Post by Klaidas on 2006-03-14
Is this really a command?

---

### Post by LKRaider on 2006-03-14
It just allows you to type several commands, using multiple lines. You start it with "(" and end the sequence of commands with ")".

Example:
```
bash:~$ (
> ls /media
> ls /mnt
> )

```

Also, you can do the same thing using a single line:
```
bash:~$ ( ls /media; ls /home; )
```

: )

---

### Post by torx on 2006-03-14
ooooooooooohh... i get it now.

thanks alot

---

### Post by sisooktom on 2006-03-14
Actually, parentheses cause the enclosed commands to be run in a subshell.  This probably isn't of much interest unless you write a lot of shell scripts, but you can illustrate by typing the command (cd /)  from your home directory.  The command succeeds, but you're in the same directory as before because the cd ran in a subshell which then exited.  

The fact that the shell gives the > prompt that lets you enter additional commands is just something it does because it knows the command isn't finished.  If your goal is just to spread a command out over multiple lines, the backslash would be a better choice IMO.

---

