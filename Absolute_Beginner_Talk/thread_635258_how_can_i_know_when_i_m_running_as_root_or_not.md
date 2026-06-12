---
title: "how can i know when i m running as root or not?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-08
`and also is there a way to "toggle" it root/non root?

---

### Post by Joeb454 on 2007-12-08
By default, everything runs as a standard user.

you can run things as root from the terminal by typing sudo in front of the command, though I wouldn't recommend it :)

Not sure if there's a way to toggle it on and off, either way I wouldn't recommend running as root

---

### Post by someoneouthere on 2007-12-08
so a good idea would be a second user with no adminstrative tasks after all?

---

### Post by t0p on 2007-12-08
If you give the command
```
sudo -s
```
you will become root.  You'll know you're root because your command prompt will look like
```
root@ubuntu:~#
```

When you want to stop being root, give the command
```
exit
```
and you'll return to your normal user status.  And the command prompt will look like
```
user@ubuntu:~$
```

Hope this helps!!

---

### Post by someoneouthere on 2007-12-08
yes.... a lot
but a good idea would be also to have a small icon on the taskbar to inform us when we are or not...(like green-red light...) what do you think?

---

### Post by t0p on 2007-12-08
> **someoneouthere said:**
> ... a good idea would be also to have a small icon on the taskbar to inform us when we are or not...(like green-red light...) what do you think?

Nah, I don't think that'd be necessary.  When you're root, your prompt is #.  When you're non-root, it's $.  Which is enough, I think, cos you're generally gonna be rooting around on the command line -  unless, of course, you're doing **gksudo** to have superuser privileges in the GUI...

---

### Post by nikoPSK on 2007-12-08
> **t0p said:**
> If you give the command
```
sudo -s
```you will become root.  You'll know you're root because your command prompt will look like
```
root@ubuntu:~#
```When you want to stop being root, give the command
```
exit
```and you'll return to your normal user status.  And the command prompt will look like
```
user@ubuntu:~$
```Hope this helps!!

well, I never knew that. Thanks!

---

### Post by Dr Small on 2007-12-08
If you wanted the prompt to be red or green, in the terminal, you could add this to your .bashrc file:
```
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Green
```

And for root to be red, just add this to /root/,bashrc:
```
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Red
```

Now when you login as root, in the terminal, you will know if you are by the red prompt.

Dr Small

---

### Post by t0p on 2007-12-08
> **Dr Small said:**
> If you wanted the prompt to be red or green, in the terminal, you could add this to your .bashrc file:
```
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Green
```

And for root to be red, just add this to /root/,bashrc:
```
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Red
```

Now when you login as root, in the terminal, you will know if you are by the red prompt.

Dr Small

Nice one Doc!! I think I might go for a red/green prompt after all!!  :)

---

### Post by nikoPSK on 2007-12-08
> **nikoPSK said:**
> well, I never knew that. Thanks!


DrSmall was laughing at me.... :( I used sudo su all the time. I knew that. And exit. But That's a different way. Whatever.:lolflag:

---

### Post by Dr Small on 2007-12-08
I just tested this, so am going to give some hindsight on how to do it.

First, we need to comment out line 26 and 29, that look like this:
```
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```
```
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

Just add a hash sign (#) at the beginning of that line.
Now, go down to line 34. which looks like this:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

Comment it out (#) and then below it, add:
```
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ ' #Red
```

Now, save and exit. Open up a terminal and type in:
```
sudo su
```
The prompt should now change colors.

Dr Small

---

### Post by LaRoza on 2007-12-08
```

whoami

```

---

### Post by nikoPSK on 2007-12-08
> **Dr Small said:**
> I just tested this, so am going to give some hindsight on how to do it.

First, we need to comment out line 26 and 29, that look like this:
```
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
``````
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```Just add a hash sign (#) at the beginning of that line.
Now, go down to line 34. which looks like this:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```Comment it out (#) and then below it, add:
```
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ ' #Red
```Now, save and exit. Open up a terminal and type in:
```
sudo su
```The prompt should now change colors.

Dr Small

cool.:lolflag:

---

### Post by nsilva on 2007-12-08
I have seen in several tutorials that for graphical commands instead of:

```
sudo <program>
```

they use 

```
gksudo <program>
```

In my case if I use sudo for both graphical and non-graphical commands it works, but in case it doesnt work for you, give **gksudo** a shot

Read some more from the Ubuntu wiki
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by someoneouthere on 2007-12-08
i am kind of new around linux... how can i edit the .bashrc file?

---

### Post by someoneouthere on 2007-12-08
silly quest.. ithink i 've done it...

---

### Post by Dr Small on 2007-12-08
> **someoneouthere said:**
> i am kind of new around linux... how can i edit the .bashrc file?
Here, I just wrote a complete tutorial on it, at my blog:
[http://php.8ez.com/drsmall/blog/?p=189](http://php.8ez.com/drsmall/blog/?p=189)

Dr Small

---

### Post by t0p on 2007-12-08
I now have Dr Small's patented RED ROOT COMMAND PROMPT.  Such a *useful* hack...  ;)

---

### Post by Dr Small on 2007-12-08
> **t0p said:**
> I now have Dr Small's patented RED ROOT COMMAND PROMPT.  Such a *useful* hack...  ;)
LOL. Please don't patent it with my name, I stole it from fluxbuntu wiki :D
[http://wiki.fluxbuntu.org/index.php?title=Favorite.bashrc](http://wiki.fluxbuntu.org/index.php?title=Favorite.bashrc)

---

### Post by Wazeem on 2007-12-08
Well for me when I try a sudo command it asks for the password but my keyboard inputs are ignored. Possibly a bug, I use the search applet and search for root where in actions it says launch terminal as root (or something to that effect).

---

### Post by Dr Small on 2007-12-08
> **Wazeem said:**
> Well for me when I try a sudo command it asks for the password but my keyboard inputs are ignored. Possibly a bug, I use the search applet and search for root where in actions it says launch terminal as root (or something to that effect).
Please read this article for a complete understanding:
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

Dr Small

---

### Post by someoneouthere on 2007-12-08
that was great thanks

---

