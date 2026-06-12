---
title: "Can't cd into my username directory"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-11-24
I want to go into my home/username directory in the terminal. I can get into the home directory by doing:

```
cd /home
```

Then when I do:

```
cd /bitm
```

it tells me "No such file or directory".

I can cd into the other folder in my home directory (lost+found), but not my username one.

What am I doing wrong? :-k

---

### Post by taurus on 2006-11-24
It should have been

```
cd bitm
```
Or better yet, "cd" by itself will drop you back to your $HOME directory no matter where you are currently...

---

### Post by scxtt on 2006-11-24
/home/bitm and /bitm are 2 different things ... there most likely (actually assuredly) is no /bitm if you're referring to ~ ...

---

### Post by BackInTimeMan on 2006-11-24
> **taurus said:**
> It should have been

```
cd bitm
```
Or better yet, "cd" by itself will drop you back to your $HOME directory no matter where you are currently...

Well, I am confused. If whilst in the home directory, I do:

```
cd bitm
```

it takes me back to my desktop prompt. Ah, you're saying "cd" and "cd bitm" takes me to "$HOME" and I think they take me to my desktop prompt. I am completely misunderstanding this somehow...

This is what I did.

I am in the terminal at my desktop prompt:

```
bitm@bitm-desktop:~$
```

and I type:

```
cd /home
```

and I am then in my "home" directory. I type:

```
ls
```

and I see the three folders in that directory, "bitm", "lost+found" and one I put there, "sysrcd". I can cd into "lost+found" and "sysrcd" but not into "bitm".

Can you put me right or is there no hope for me?  :)

---

### Post by Arisna on 2006-11-24
When you launch a terminal, you're almost certainly already in /home/bitm.  The "bitm-desktop" is the hostname of the machine, not the working directory.  The "~" is the working directory and stands for your home folder, /home/bitm.

---

### Post by BackInTimeMan on 2006-11-24
> **scxtt said:**
> /home/bitm and /bitm are 2 different things ... there most likely (actually assuredly) is no /bitm if you're referring to ~ ...

Now I am even more confused... :-?

---

### Post by taurus on 2006-11-24
Let's backup a little here...

```
bitm@bitm-desktop:~$
```
bitm is your login name and bitm-desktop is the name of your machine, the one that you assigned when you install it.  ~ means that you are currently in your $HOME directory, aka /home/bitm!!!

So if you do "cd /home", and you want to get into bitm, then you need to use "cd bitm" instead of "cd /bitm" because /bitm mean top level and then bitm which you don't have.  bitm in under /home, not /...

---

### Post by Brownedwg89 on 2006-11-24
~ is short for /home/username
```
bitm@bitm-desktop:~$
```
means the user "bitm" using the computer named "bitm-desktop" in the directory "~"

---

### Post by Arisna on 2006-11-24
Okay, a quick explanation.  "/" is the top level (root) directory of your system.  Everything on your computer is stored somewhere under it.  There is a directory called "home" under "/".  The full path to it is "/home".  What is generally known as "your home folder" is in turn a subdirectory of "/home" called "/home/bitm".  This is how GNU/Linux and other Unix-like operating systems organize files.  See the link below for the gory details of this. :)

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by BackInTimeMan on 2006-11-24
> **Arisna said:**
> When you launch a terminal, you're almost certainly already in /home/bitm.  The "bitm-desktop" is the hostname of the machine, not the working directory.  The "~" is the working directory and stands for your home folder, /home/bitm.

Yay! The penny has dropped, thank you  :D

---

### Post by BackInTimeMan on 2006-11-24
Thanks everyone, I *really* get it now, honest...  :)

Cheers.

---

### Post by po0f on 2006-11-25
BackInTimeMan,

If your terminal prompt doesn't let you know where you're at in the filesystem  for whatever reason (the "bitm@bitm-desktop:~$" part of the terminal, which is usually in "username@host:current_working_directory$" format), you can always issue a quick `pwd` (note: commands you type in bold):
```
bitm@bitm-desktop:~$ **pwd**
/home/bitm
bitm@bitm-desktop:~$ **cd /usr/lib**
bitm@bitm-desktop:/usr/lib$ **pwd**
/usr/lib
bitm@bitm-desktop:/usr/lib$ 
```
to see where you're at.  The default terminal prompt will let you know what directory you are currently in.  As mentioned before, "~" is shorthand for current user's home directory.  If there were other users on the system, you could `cd` into their directory with ~*username*, for example:
```
bitm@bitm-desktop:~$ **cd ~joe_user**
bitm@bitm-desktop:/home/joe_user$ 
```

Hope this helps.

---

### Post by BackInTimeMan on 2006-11-25
po0f,

Good tips, thanks very much!

---

