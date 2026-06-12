---
title: "very little help?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by strider* on 2008-01-15
about using vi in ubuntu? i'm very new to it, and i dont know how things goes around.. i am going to edit something using it but i'm only viewing it.. wat should i do?

---

### Post by LaRoza on 2008-01-15
[http://www.vim.org/](http://www.vim.org/)

(Press "i" to go into edit mode)

Search the web for Vi(m) tutorials.

---

### Post by machoo02 on 2008-01-15
Perhaps you should use something a little more user friendly first, such as gedit.  If you are dead set on using vi, check out a guide such as [this]("http://www.cs.fsu.edu/general/vimanual.html").

---

### Post by mdpalow on 2008-01-15
I personally don't use vi, so...

you can always just:

```
sudo gedit /enter/path/to/file/filename
```

---

### Post by LaRoza on 2008-01-15
> **mdpalow said:**
> I personally don't use vi, so...

you can always just:

```
sudo gedit /enter/path/to/file/filename
```

No, use "gksudo gedit", not sudo.

---

### Post by nikoPSK on 2008-01-15
> **LaRoza said:**
> No, use "gksudo gedit", not sudo.

I second that, But I prefer nano or vim. :)

---

### Post by LaRoza on 2008-01-15
> **nikoPSK said:**
> I second that, But I prefer nano or vi. :)

I prefer vim, but I was correcting the post I quoted.

---

### Post by strider* on 2008-01-15
wow.. i really appreciated your help guys ;)... thanks!

---

### Post by oldos2er on 2008-01-15
> **strider* said:**
> about using vi in ubuntu? i'm very new to it, and i dont know how things goes around.. i am going to edit something using it but i'm only viewing it.. wat should i do?

 In a terminal, type "sudo apt-get install vim-runtime". Then type "vimtutor." The tutorial takes about 20 - 30 mins.

---

### Post by apostate on 2008-01-15
Plus Ubuntu comes with Tiny- VI which doesn't always behave as tutorials expect ti too. It is feature slim. I'd use Synaptic to download the full VIM editor package, so you get all the enhancements.

Remember VI is modal, so to edit anything you hit "i" for insert, and ':' to go back to command mode.

Good luck!

---

### Post by mdpalow on 2008-01-18
> **LaRoza said:**
> No, use "gksudo gedit", not sudo.

What exactly is wrong with sudo?

---

### Post by zipperback on 2008-01-18
> **strider* said:**
> about using vi in ubuntu? i'm very new to it, and i dont know how things goes around.. i am going to edit something using it but i'm only viewing it.. wat should i do?



vi is a very powerful editor once you get to know it.

Here is a link to a cheat sheet for it.

[http://www2.cs.uidaho.edu/~rinker/ed03.pdf](http://www2.cs.uidaho.edu/~rinker/ed03.pdf)

If you want something a little simpler to use, might I suggest using pico?

```
pico filename.txt
```

- zipperback
:popcorn:

---

### Post by nikoPSK on 2008-01-18
nano is nice too. :)

---

### Post by jordanmthomas on 2008-01-18
> **mdpalow said:**
> What exactly is wrong with sudo?

It can mess with your .Xauthourity and .ICEAUTHORITY (and others, maybe .dmrc?)
Anyway, all that happens is permissions on some files in your home directory get messed up, causing some ugly (but easily fixable) annoyances.
This doesn't always happen, but basically using sudo will sometimes cause the user's configuration files to be used instead of root's (I believe firefox does this, and things can get hairy there too)

gksudo doesn't do this, and thus you should use it when you need a GUI program to have root access.  sudo's fine for command-line things that don't connect to your xserver.

---

