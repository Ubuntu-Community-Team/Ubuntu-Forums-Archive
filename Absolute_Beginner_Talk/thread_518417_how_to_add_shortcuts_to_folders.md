---
title: "how to add shortcuts to folders?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by fflarex on 2007-08-05
When I first made the switch to Ubuntu/Linux, I was baffled by the lack of shortcuts until I discovered that launchers took care of this. At least when it comes to applications. Now, after 2 months of exclusively using Ubuntu, I miss shortcuts again. Why? Well, I can't figure out how put a link/shortcut/launcher in my home folder that redirects somewhere else. I want it to look like my music folder is in my home directory, even though it's on an entirely separate partition. How can I do this?

---

### Post by arijarot on 2007-08-05
right click on the object and select "make link"; a link appears...there is your shortcut:) 

put this link (shortcut) wherever you want...

---

### Post by fflarex on 2007-08-05
Thanks...

I feel like an idiot now. I've definately done way more advanced stuff than this, and yet here is the most basic thing ever that I couldn't figure out for the life of me.

---

### Post by arijarot on 2007-08-05
I think we've all had oversights at some time--ESPECIALLY on the most basic things as we give them no thought or effort.

---

### Post by fflarex on 2007-08-07
Okay, I guess I'm having more troubles adding shortcuts. I want to add the aforementioned music shortcut to my home folder, but it says I'm not allowed or "Operation not permitted" or something like that when I right click and select 'make link'. I got all the permissions sorted out in another thread (or so I think), but it still won't let me. Could it be because it's FAT32? I can't imagine that would make too much difference, but it's the only thing I can think of right now.

---

### Post by arijarot on 2007-08-08
open up a terminal and type

```
sudo nautilus
```

this will give you root permissions, (so be careful!)

---

### Post by hyper_ch on 2007-08-08
Or from the cli you can do this:

Go to where you want the shortcut to be (e.g. Desktop):
```

cd /home/USER/Desktop

```

```

sudo ln -s /path/to/dir NAME

```

This will make a shortcut named "NAME" on your desktop and it will point to /path/to/dir

---

### Post by fflarex on 2007-08-08
@arijarot: Didn't work. Something is messed up here besides permissions. Like I said before, I'm fairly sure folder/file permissions were fixed in another thread of mine.

@hyper_ch: Worked perfectly, though I must say I'm little annoyed at having to use the terminal to do this. Oh well.

---

### Post by hyper_ch on 2007-08-08
well, I have always (at least one) terminal open and it's quicker that way... just being used to symlink a lot on a server ;)

---

### Post by arijarot on 2007-08-08
Glad to see it worked through the cli. What error did you get when using nautilus as root?

---

### Post by fickendichdu on 2007-08-28
You can also create a launcher that points to a file in the location type where you want it to go.  I do this at work for some of the shares I access constantly.

---

### Post by fickendichdu on 2007-08-28
If you are mapping to a hidden drive do not use the dollar sign it seems to confuse nautilus use %24 and that will let the link work.  Not sure if that is a bug or not.

---

### Post by skrimpy on 2007-09-27
> **arijarot said:**
> right click on the object and select "make link"; a link appears...there is your shortcut:) 

put this link (shortcut) wherever you want...

Thank you!  Searched for this and you answered my question.  Now I feel like a dummy, but I'm a happy one! :KS

---

### Post by arijarot on 2007-09-27
> **skrimpy said:**
> Thank you!  Searched for this and you answered my question.  Now I feel like a dummy, but I'm a happy one! :KS

Glad to have helped you :KS

---

### Post by gnudoc on 2007-09-27
> **fflarex said:**
> 
@hyper_ch: Worked perfectly, though I must say I'm little annoyed at having to use the terminal to do this. Oh well.

you'll soon find that, although  few things absolutely *need* the terminal these days, there still are (and always will be) loads of things that are just much easier, quicker and slicker to do via the terminal, once you get even slightly comfortable with it.

my advice to all ubuntu users that have reached the degree to competence that you seem to have, is to get comfortable with using the terminal. start with just doing one or two things from there - do your upgrades from there, try handling some files from there. it's surprising how quickly you get up to speed with it. i'm not sure if there's a howto for basic command-line skills in these forums - if not, i'll maybe write one. (there's a few good pages at the community docs site - [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=command+line&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=command+line&titlesearch=Titles) will give you them)

---

