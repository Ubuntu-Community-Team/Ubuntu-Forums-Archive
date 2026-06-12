---
title: "Where's Wine?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-06
I've installed Wine via the instructions on the website AND with the add/remove programs. I can't find it or use it, I really don't even know what I'm doing. Is it a program, or does it just make stuff work? Because neither of those seem to be happening. =/

---

### Post by maxamillion on 2007-04-06
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by jhenager on 2007-04-06
You can also use the Wine file browser, by running winefile in a terminal. Clicking the C:\ button in the toolbar will open a window where you can browse the virtual Windows drive created in .wine. Doubleclicking an executable in the Wine file browser will run it in Wine.

---

### Post by Biscuitpie on 2007-04-06
Thanks. :) One more question while the thread is here. How do I find my IP in regards to my router? like it's usually 101-109. In windows I would just use ipconfig in command prompt. :O

---

### Post by maxamillion on 2007-04-06
```
ifconfig
```

---

### Post by sirhalos on 2007-04-06
The easiest way is after WINE is installed just double click an EXE file. You should get a box come up asking you what program you want to use, go to the bottom where you can select a program and just type wine and click OK. That will set the command wine as default to run an EXE. Now after that just double click an EXE program and you are ready to go.

---

### Post by Biscuitpie on 2007-04-06
> **maxamillion said:**
> ```
ifconfig
```

```
andrew@andrew-laptop:~$ ipconfig
bash: ipconfig: command not found
```

---

### Post by Biscuitpie on 2007-04-06
In the winefile browser I can't find the utorrent folder.

---

### Post by Maestro23 on 2007-04-06
> **Biscuitpie said:**
> ```
andrew@andrew-laptop:~$ ipconfig
bash: ipconfig: command not found
```

For ipconfig, you need to install net-tools.

> sudo aptitude install net-tools

Installs other networking tools as well.  Can search for it in Synaptic and read about it.

---

### Post by Biscuitpie on 2007-04-06
> **Maestro23 said:**
> For ipconfig, you need to install net-tools.



Installs other networking tools as well.  Can search for it in Synaptic and read about it.
I got it installed. How do I use it?

---

### Post by Biscuitpie on 2007-04-06
> **Biscuitpie said:**
> I got it installed. How do I use it?

:( I need to know for port forwarding.

---

### Post by Punker on 2007-04-06
I don't know I mean dispute my thoughts about automatrix their not all bad I think you should use it 
[www.getautomatix.com/](www.getautomatix.com/)

---

### Post by mdsmedia on 2007-04-06
> **Biscuitpie said:**
> :( I need to know for port forwarding.Where you typed "ipconfig" use ifconfig...."f" instead of "p"

---

### Post by Biscuitpie on 2007-04-06
Thanks. :)

---

### Post by n3tfury on 2007-04-08
> **Biscuitpie said:**
> ```
andrew@andrew-laptop:~$ ipconfig
bash: ipconfig: command not found
```

perhaps you need to downgrade your resolution or get glasses.  or both ;)

---

### Post by Biscuitpie on 2007-04-08
> **n3tfury said:**
> perhaps you need to downgrade your resolution or get glasses.  or both ;)

It's hard to read my computer with contacts, as it starts to blur. So, yes, I need my glasses. :P

---

### Post by psychok7 on 2007-04-08
i cant browse anything on my program files.. only a folder called common files is in there... can anyone help me solve this problem?

---

