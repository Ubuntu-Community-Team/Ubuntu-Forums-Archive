---
title: "Basic commands"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by otetiani on 2006-03-01
I was just wondering if anyone could point me to a link or book to help me understand some basic commands.

I know what some do, but why?  What do they mean? Or is it just a name?

Examples:

sudo: I know it allows me to act as root, even though I'm not logged in as root

dpkg: I think it tells there is a command for packages such as install (dpkg -i)

wget: get file from the web?

apt-get: no idea, but it's used a lot for removing and installing files.

Basically I'm looking for a way to remember the commands, some I can makeup a reason for what they do, but like apt-get I have no idea.:(

---

### Post by engla on 2006-03-01
I can plug this link again:
[http://linuxcommand.org/](http://linuxcommand.org/)
It's a very basic tutorial about commands.. doesn't cover the ones you mentioned, but it's all probably good to know.

And I can mention possibly the best command of all, 'man' (for manual).

```
man command
```
Opens a help page about the command 'command'. Use arrow keys to read, 'q' to quit.

You can also use
```
man -k "search term"
```To search for commands related to "search term".

---

### Post by Coelocanth on 2006-03-01
[Here's](http://www.ss64.com/bash/) another link that may prove useful as well.

---

### Post by RaiSuli on 2006-03-01
apt-get is only used for applications and updates you can get from the repositories you specified in etc/apt/sources.list. Apt means "advanced package tool".

dpkg is used to install deb packages, but doesn't resolve dependencies.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) is a good place to learn more about the shell. Helped me a lot. :)

EDIT: must learn to type faster.

---

