---
title: "Weird characters in the linux consoles and lines not drawn correctly"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by fakie_flip on 2007-06-05
Hello. I need some help. When I launch midnight commander or finch from a linux console such as tty5, it displays strange characters, happy faces, etc. and does not display the lines correctly. How can it be fixed?

To see what I mean, install midnight commander.

```
sudo apt-get install mc
```

Switch to a linux console that isn't running x by pushing these keys.

```
control alt f1
```

Login and type mc to launch midnight commander.

[http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg](http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg)

---

### Post by BatsotO on 2007-06-06
Try sudo dpkg-reconfigure console-setup

change the console to be use from fixed to vga, I think this will work

---

### Post by fakie_flip on 2007-06-06
> **BatsotO said:**
> Try sudo dpkg-reconfigure console-setup

change the console to be use from fixed to vga, I think this will work

That made it worse than before. Have you tried it on your computer? How do I get the default settings back for all those questions that the command asks?

---

### Post by fakie_flip on 2007-06-06
Nevermind about changing it back to default. I found this from the man page.

```
chris@ubuntu:~$ sudo dpkg-reconfigure --default-priority console-setup
Password:
 * Saving console font and keymap for next boot...                       [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
chris@ubuntu:~$
```

---

### Post by fakie_flip on 2007-06-06
I fixed the problem. Incase anyone else is having the same problem, he or she can read what I wrote on a mailing list on how I fixed it.

[http://satlug.org/pipermail/satlug/2007-June/048866.html](http://satlug.org/pipermail/satlug/2007-June/048866.html)

---

### Post by fakie_flip on 2007-06-06
I made one correction. Instead of running this.

echo "export LANG=en_US.ISO-8859-1" >> .bashrc

You should run this.

echo "export LANG=en_US.ISO-8859-1" | sudo tee -a /etc/bash.bashrc

so that the problem is fixed for all users, not just the user you are logged in as.

---

### Post by BatsotO on 2007-06-06
> **fakie_flip said:**
> That made it worse than before. Have you tried it on your computer? How do I get the default settings back for all those questions that the command asks?

It does work on my pc, but sorry for the mishaps.

---

### Post by GoofYas007 on 2007-12-16
Perfect solution.
Thnx a lot :)

---

### Post by lukanova on 2008-06-28
another solution to this is to create an alias:

alias mc='export LANG=en_US; mc'

this will first switch the LANG locale to en_US (or if you prefer you can use en_US.ISO-8859-1) and then run mc. this way your default console stays utf8.

you can add alias definition to bashrc (user's or global/systemwide):

echo "alias mc='export LANG=en_US; mc'" >> .bashrc

echo "alias mc='export LANG=en_US; mc'" | sudo tee -a /etc/bash.bashrc

i had problems with strange characters with Midnight Commander in Eterm (xterm/gnome-terminal) have no problems. this helped me.

---

