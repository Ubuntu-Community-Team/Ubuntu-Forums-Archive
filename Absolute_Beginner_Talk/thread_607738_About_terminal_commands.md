---
title: "About terminal commands"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bluespider on 2007-11-09
Is there a list  or manual somewhere about all the commands you can put into the terminal and what they do ?? Could someone please  give me a link to it or something, Thank you.

---

### Post by amingv on 2007-11-09
Hi,

I have not been able to find a decent command list for dash, but there's a [good one for bash]("http://www.ss64.com/bash/"). Note that not all bash functions will work with dash.

You may also be interested in [this]("http://tiswww.case.edu/php/chet/bash/bashref.html").

---

### Post by Harpoon on 2007-11-09
Here is a resource you may find useful:
[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by bluespider on 2007-11-09
Im am sorry I do not know what you are referring to by bash and dash could you explain please?

---

### Post by Dr Small on 2007-11-09
> **bluespider said:**
> Is there a list  or manual somewhere about all the commands you can put into the terminal and what they do ?? Could someone please  give me a link to it or something, Thank you.
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

---

### Post by overdrank on 2007-11-09
> **bluespider said:**
> Is there a list  or manual somewhere about all the commands you can put into the terminal and what they do ?? Could someone please  give me a link to it or something, Thank you.

Hi, here is a couple of links for command line
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

Good luck! :KS

---

### Post by svalding on 2007-11-09
There are different types of terminal "languages" typically users will use the bash shell, which is the default in Ubuntu. If you have no real plans for doing any scripting for different linux platforms, then you will not need to know anything further than that you have a bash shell. 

There is a wonderful tutorial on the terminal floating around these forums, I will see if I can dig it up for you. 

Also, the command to get you started in some research would be the man command. It pulls a manual into the terminal that you can search for virtually any command within the linux os. very cool.

---

### Post by Dr Small on 2007-11-09
> **overdrank said:**
> Hi, here is a couple of links for command line
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

Good luck! :KS
overdrank always has a more informational post than I :p
I think I need to enhance my bookmarks a bit ;)

---

### Post by qamelian on 2007-11-09
> **svalding said:**
> There are different types of terminal "languages" typically users will use the bash shell, which is the default in Ubuntu.

The default system shell in Ubuntu is dash, not bash and has been since Ubuntu 6.10 "Edgy Eft". Ubuntu only uses bash as the default login shell.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by amingv on 2007-11-09
> **bluespider said:**
> Im am sorry I do not know what you are referring to by bash and dash could you explain please?

[Bash]("http://en.wikipedia.org/wiki/Bash") and [Dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell") are just shell "versions" (so to speak). I do not know in-depth about their differences but I am aware that bash is an advanced shell with many functions while dash is a more compact version. Dash is used by default in Ubuntu as of v6.10 but you can use bash commands by typing

```
bash command_name
```

or adding

```
#!/bin/bash
```

as a header for your scripts.

---

### Post by overdrank on 2007-11-09
> **Dr Small said:**
> overdrank always has a more informational post than I :p
I think I need to enhance my bookmarks a bit ;)

Thanks Dr small and I still have no idea what I am doing lol :lolflag:

---

