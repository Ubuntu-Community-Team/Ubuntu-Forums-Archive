---
title: "Console: Alternate last command?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-11
Hello,

If I want to bring up the last command, I would use the Up key.  I use the last command a lot especially for doing the same task.  The thing is, my fingers have to leave my homerow and look at where the up key is because its way to far for my right pinky to reach.  Then I would have to look at the keyboard again to return to the homerow.  This is a major setback in keyboarding; having to look at my keyboard.

So my question is: Is there an alternate command or shortcut that I can use without having me to leave the homerow?

---

### Post by 23meg on 2005-11-11
You should be able to do this by putting the alternate keycodes to your ~/.inputrc file. A google search should turn some results.

---

### Post by Kvark on 2005-11-11
Ctrl+P also brings up the previous command.

---

### Post by apjone on 2005-11-11
[QUOTE=Kvark]Ctrl+P also brings up the previous command.[/QUOTE]

ctrl+P previuos
ctrl+N next

---

### Post by 23meg on 2005-11-11
A nice trick: put
```

"\e[5~": history-search-backward
"\e[6~": history-search-forward

```
into your ~/.inputrc and you can do a bash history search with PageUp/PageDown. I don't know how I lived without this until I discovered it.

---

### Post by ramdisc on 2005-11-12
There is no ~/.inputrc in my system.  I had to make one.  So it's blank.

```

"shitf+<": history-search-backward
"shift+>": history-search-forward

```

This didn't work.  How do I make shift + < and shift + > work?

---

### Post by 23meg on 2005-11-12
I think you can get the keycodes for any key using the "showkey" command and put them in the .inputrc file. "man showkey" should give you the details.

---

### Post by ramdisc on 2005-11-12
I got returned with:
```

Couldn't get a file descriptor referring to the console
```

---

### Post by 23meg on 2005-11-12
It might be because X is interfering; try running showkey in a virtual terminal (Ctrl+Alt+F1).

---

