---
title: "keyboard shortcuts"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by cmagan on 2007-04-25
my keyboard shortcuts dont work
ctrl+c dont copy and ctrl+v dont paste, for exmple. 
where do i config that? (prefrences>keyboard shortcuts has very limited options...)

thanks

---

### Post by viciouslime on 2007-04-25
What are you trying to copy and paste to and from? If you close the window you copied from before you paste it somewhere, then it will have this effect.

---

### Post by cmagan on 2007-04-25
anyway, where do i set the keyboard shortcuts?

---

### Post by doomster on 2007-04-25
to edit keybord shortcuts you will use the embedded Keyboard Shortcuts utility from system Preferenced menu.... i have noticed that paste shortcut doesnt work on terminal window.

---

### Post by paparucino on 2007-04-25
> **doomster said:**
> to edit keybord shortcuts you will use the embedded Keyboard Shortcuts utility from system Preferenced menu.... i have noticed that paste shortcut doesnt work on terminal window.
yes, it works only if you use the mouse

---

### Post by fatphilthethird on 2007-04-25
> **paparucino said:**
> i have noticed that paste shortcut doesnt work on terminal window.

It does, but it's *ctrl+**shift**+v*

Fat

---

### Post by Skrynesaver on 2007-04-25
> **fatphilthethird said:**
> It does, but it's *ctrl+**shift**+v*

Fat

there is a good reason for this, when you want to send a character such as CTRL-M to a command and not have it interpreted as a carriage return you can first hit CTRL-V, thus if you wanted to strip ^M from the end of a textfile that originated on an MS file system you could 
```

sed 's/^M//' filename.txt >>filename.clean.txt

```

---

### Post by wat3r on 2007-04-25
> **Skrynesaver said:**
> there is a good reason for this, when you want to send a character such as CTRL-M to a command and not have it interpreted as a carriage return you can first hit CTRL-V, thus if you wanted to strip ^M from the end of a textfile that originated on an MS file system you could 
```

sed 's/^M//' filename.txt >>filename.clean.txt

```

You can also just press the middle mouse button, or "scroll button". Another good feature is that you don't have to do any copy commands. Let's say you for example read an howto, and you want to perform a command that is in that howto. Then you just mark the text you want to execute in terminal, open the terminal window and press the middle mouse button or ctrl+shift+v, and you will have the text you marked pasted into terminal. This works with text marked inside the terminal also. I guess it works between all programs, not just FF -> Terminal, but I can't say that for sure, since i'm not by my Ubuntu computer ATM.

---

