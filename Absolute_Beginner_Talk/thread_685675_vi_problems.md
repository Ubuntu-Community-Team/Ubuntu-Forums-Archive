---
title: "vi problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-02-02
I have used Fedora core ages ago and I used vi from the command line. When using vi in fedora i used my arrow keys to move down the file but when I do that using vi in ubuntu it does not move down the file it adds the letters A when I go up and B when I try to go down.

Any ideas?

---

### Post by Presto123 on 2008-02-02
Best advice, don't do it! :P

Really, to navigate to the file extensions, you can type:

```
cd filename/file/etc
```

There could be an easier way, but I believe I am a sucker for taking the long way around...everything...

So, here's what I usually do:

```
cd filename
dir
blah blah blah.tar
cd blah blah blah.tar
etc, etc
```

---

### Post by appleimac on 2008-02-02
Hi thanks for the reply.

You have lost me whats changing directory got to do with using VI editor in the command line?

---

### Post by Presto123 on 2008-02-02
OH! LOL, never mind. Pardon me, I assumed the wrong thing. Looks like someone else will need to help you on this one.

---

### Post by scorp123 on 2008-02-02
> **appleimac said:**
>   When using vi in fedora i used my arrow keys to move down the file but when I do that using vi in ubuntu it does not move down the file it adds the letters A when I go up and B when I try to go down.  What terminal program (assuming you use a terminal program for X11 here, e.g. "xterm" or something like that) and what keyboard settings (German? US English? Russian? ...?) are you using? What CPU platform are you using (you are on a more or less standard PC right? Or are you using e.g. a SUN machine?)

All these things can have an influence.

As for vi ... the one that gets installed on Ubuntu is in fact "vim-tiny" which only has the most basic features. It sucks in my opinion. The first thing I do is to get the full featured version:
```
sudo apt-get update
sudo apt-get install vim-full
```

Also, I enable syntax highlighting so it's always on per default and I add an extra option that will make copy & paste a bit easier (the "vim" version on Ubuntu 7.10 "Gutsy" behaves sometimes in strange ways without this option when you paste text into it ... ):
```
sudo vim /etc/vim/vimrc
``` ... then find and change / add these lines (marked in red): ```
...
...
" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
[COLOR="Red"]syntax on
set paste[/COLOR]
...
...
```

---

### Post by appleimac on 2008-02-02
Thankyou very much for that bit of info. Very Helpful :D

---

