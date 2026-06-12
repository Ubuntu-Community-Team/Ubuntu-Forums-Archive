---
title: "Can you tell me how to do this in Terminal?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-28
Actually, it is probably not done in Terminal. Anyway, when you are in Terminal, you can use your up and down arrows on your keyboard to see former commands you have typed in. Is there a way to delete the entire list or any part of it? I suspect it is a file somewhere that can be opened and edited.

Thanks for any suggestions that will help me to do this. 
kh

---

### Post by joft on 2007-04-28
Yes, all the commands are saved in the file ~/.bash_history (if you use bash as your shell) and AFAIK is saved on logout/exit of the shell.

---

### Post by Xyhthyx on 2007-04-28
You can disable the feature entirely if you want by doing the following:

```
rm -f ~/.bash_history
gedit ~/.bash_profile
```

    * Add the following: 

```
export HISTFILESIZE=4
unset HISTFILE=5

# Change this to a reasonable number of lines to save, I like to save only 100.
export HISTSIZE=1

# Ignores duplicate lines next to each other
export HISTCONTROL=ignoredups
```

This will disable Bash history for the user, retaining keystroke history and recall to use while limiting recall history to 100 lines. This will also not record duplicate lines next to each other.

---

### Post by kittyhawk63 on 2007-04-28
What I was really looking for is a file in Nautilus that I can edit. Is there one of these?
kh

---

### Post by K.Mandla on 2007-04-28
You should be able to edit .bash_history in Nautilus. It's hidden, so it might not show up at first.

If you just want to clear it,

```
history -c
```
empties your history completely, if that's useful. I make a point of doing that before I sell a machine with Ubuntu on it. :mrgreen:

---

### Post by kittyhawk63 on 2007-04-28
> **K.Mandla said:**
> You should be able to edit .bash_history in Nautilus. It's hidden, so it might not show up at first.
If you just want to clear it,
```
history -c
```empties your history completely, if that's useful. I make a point of doing that before I sell a machine with Ubuntu on it. :mrgreen:

I ran the hidden-c. I don't find bash in Nautilus. Is it hidden. How do I unhide it if it is?
kh

---

### Post by kittyhawk63 on 2007-04-28
.

---

### Post by DezSP on 2007-04-28
Go to your home folder, press Ctrl+H (or go to View -> Show hidden files), this will show all files beginning with a . (period), which will hide by default (even in terminal). Double-click the file and you can edit it. But typing gedit .bash_history does that anyway, so I don't really see why you need Nautilus for this.

---

### Post by kittyhawk63 on 2007-04-28
> **DezSP said:**
> Go to your home folder, press Ctrl+H (or go to View -> Show hidden files), this will show all files beginning with a . (period), which will hide by default (even in terminal). Double-click the file and you can edit it. But typing gedit .bash_history does that anyway, so I don't really see why you need Nautilus for this.

Only because I didn't know what I needed to type in terminal. Thanks for the instructions.

Edit: That didn't show me the the commands lines that I had typed in after I ran **history -c**.
I ran it again and it worked. Sorry for that.
Thanks again.
kh

---

### Post by fakie_flip on 2007-06-11
> **kittyhawk63 said:**
> Only because I didn't know what I needed to type in terminal. Thanks for the instructions.

Edit: That didn't show me the the commands lines that I had typed in after I ran **history -c**.
I ran it again and it worked. Sorry for that.
Thanks again.
kh

adding history -c to .bash_logout should clear your history each time you logout

---

### Post by kittyhawk63 on 2007-06-11
> **fakie_flip said:**
> adding history -c to .bash_logout should clear your history each time you logout

Thanks. I don't want to clear it. I just want to edit it and eliminate all the lines where typing errors appear, redundant lines appear, and lines I no longer need. I keep basic and repetitive lines so that it saves me from having to retype them each time I need them and to avoid typing errors which then require retyping.
Thanks again. I've been able to do this with your clear instructions.
kh

---

### Post by rich.bradshaw on 2007-06-11
Did you know that pressing ctrl-R lets you searh the whole history?

Did you know that adding 
export HISTCONTROL=ignoreboth

to [COLOR=green][FONT=monospace].bash_profile [COLOR=Black]will ignore identical lines that are next to each other?

To do that,

gedit ~/.bash_profile

then type the export line above at the bottom and save. Then if you were to type ls twice in a row, it won't keep both in the history...
[/COLOR][/FONT][/COLOR]

---

### Post by Bluecircle on 2007-06-16
Nice, thanks!

---

### Post by fakie_flip on 2007-06-24
> **Bluecircle said:**
> Nice, thanks!

Try this.

echo "export PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\[\033[40;33m\]\w\[\033[34m\]\$\[\033[m\] '" | tee -a ~/.bashrc

Now close the terminal and open a new one.

Cool huh?

It looks better if you change your background to black.

---

