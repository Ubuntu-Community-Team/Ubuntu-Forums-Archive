---
title: "Alias"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Nxion on 2007-04-05
I was wondering how to create aliases for my apps and what not. I have looked and I cannot find a clear description on how to do it. Can any one please help me  ?

---

### Post by taurus on 2007-04-05
What alias for your apps do you mean?  Can you give an example what you want to do?  If you want to create an alias, do it in ~/.bashrc.

```
alias l="ls -la"
```

---

### Post by Nxion on 2007-04-05
I want to create a alias for my Sirius radio, So I did this,


```
alias sirus="gnome-terminal -x /usr/bin/sipie"
```

Yes I know i spelled Sirius wrong. 

That is my next question, How do I fix it. I looked at the .bashrc file and I didn't see my alias that I made. Do I have to log in and log out ?

Thanks

---

### Post by taurus on 2007-04-05
Did you type that line from a prompt?  If that's the case, then you have to type it in every time you open a terminal or log in since it only applies for the terminal that you type it in.  Therefore, I recommend you add it to ~/.bashrc so you can call it anytime you want.

---

### Post by Nxion on 2007-04-05
Thanks I will add them directly :)

---

### Post by Nxion on 2007-04-05
One more question.

After I add the alias to the .bashrc do I have to log out and log in for it to take affect ?

---

### Post by drs305 on 2007-04-05
Once you have saved the file, just close any terminal windows you have open. When you open a new terminal it will read your .bashrc file and any aliases you've saved there. No need to reboot.

---

### Post by taurus on 2007-04-05
Or just run this command from the same terminal.

```
source ~/.bashrc
```

---

### Post by Nxion on 2008-05-02
Thanks for the help !.

---

