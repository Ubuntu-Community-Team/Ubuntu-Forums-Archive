---
title: "Linux Command problem"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by daisycool on 2008-01-23
hi all,
i just installed an application into my '**/opt**' directory, then i wanted to make the command global, so i created a symbolic link inside **/usr/local/bin**
what i did is like following:

[B]$ sudo cp -R /home/software/maven /opt
$ sudo ln -s /opt/maven/bin/maven /usr/local/bin/maven[/B]

and when i type in '$ maven' and press enter, i got an exception says:
***Exception in thread "main" java.lang.NoClassDefFoundError: com/werken/forehead/Forehead***

when i do:
**'$ /opt/maven/bin/maven**', it works.

then i removed the symbolic link from '/usr/local/bin':
**$ sudo rm /usr/local/bin/maven**

here comes the problem. as the symbolic link has been removed, when i type in '$ maven', it should show exception like: 
**bash: abc: command not found**

but what actually shown is:
**bash: /usr/local/bin/maven: No such file or directory**

does anyone know why it's happening? please help me, your help is appreciated!

best regards

---

### Post by K.Mandla on 2008-01-23
Moved to Absolute Beginner Talk. :)

---

### Post by Dr Small on 2008-01-23
Well, it looks as if it has a problem with the symbolic link, (which I don't understand why), but you could always make an alias that said this:
```
alias maven="/opt/maven/bin/maven"
```

Dr Small

---

### Post by mali2297 on 2008-01-23
> **daisycool said:**
> 
here comes the problem. as the symbolic link has been removed, when i type in '$ maven', it should show exception like: 
**bash: abc: command not found**

but what actually shown is:
**bash: /usr/local/bin/maven: No such file or directory**

does anyone know why it's happening? please help me, your help is appreciated!


I have had similar experiences after removal of programs. It was only temporarily though. I think it will get back to normal after you reboot the system, or it might be enough to restart the shell.

---

