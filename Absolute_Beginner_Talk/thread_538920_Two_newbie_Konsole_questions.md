---
title: "Two newbie Konsole questions"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-30
Hi! I have two newbie questions about the Konsole on Kubuntu 7.04:

1) Is there a keyboard short cut inside the Konsole that opens a new shell? (i.e that does exactly Session->New Shell)

2) If someone put some code here on this forum (or any other site), and I copy it (by selecting it and then Control+C),how can I paste that text inside the vi editor?(i.e, I open some file with "vi SomeFile.txt", and I want to paste the text I've copied with Control+C from the web somewhere in that file). I'm a vi newbie, but I've seen how to copy/paste inside the opened file, but not having something on the control+C buffer.


Thank you very much for your help!

---

### Post by undertherift on 2007-08-30
#1- i haven't found this.  I tired to set up the key bindings in KDE, but they never seemed to work.  However, there is an app called xbindkeys, which allows you to assign commands to keys inside your X windows.  That was my previous work around.

#2 is shift+insert.

---

### Post by reckless2k2 on 2007-08-30
vi isn't friendly for that copy feature you are looking for. i don't think you can do that with nano either. that might be only for a gui based editor like gedit or kedit. 

as far as keyboard shortcuts, that's in the kcontrol menu you can bind keys to start programs. if you have konsole open, hitting alt keys navigating is what you are looking for. i think that's what you talking about.

---

### Post by quux on 2007-08-30
> 
1) Is there a keyboard short cut inside the Konsole that opens a new shell? (i.e that does exactly Session->New Shell)


Yap... no problem. The default shortcut for opening a new shell in Konsole is "Ctrl+Alt+N" or "Ctrl+Shift+N". As someone already mentioned before you can get an overview/change all keyboard shortcuts in "Settings -> Configure Shortcuts".

> 
2) If someone put some code here on this forum (or any other site), and I copy it (by selecting it and then Control+C),how can I paste that text inside the vi editor?(i.e, I open some file with "vi SomeFile.txt", and I want to paste the text I've copied with Control+C from the web somewhere in that file). I'm a vi newbie, but I've seen how to copy/paste inside the opened file, but not having something on the control+C buffer.


As long as you are in INSERT mode in vi this should be no problem using Konsole's "paste" function. The default shortcut is "Shift+Insert".

---

### Post by asmoore82 on 2007-08-30
FYI ~ you may want to make sure you have the full vim editor installed ...

Ubuntu comes with a light-weight look-a-like but not exactly act-like 'vim-tiny'
not sure about "Kubuntu" but I would assume the situation is the same ...

```
~ $ sudo apt-get install vim
```

---

### Post by fredscripts on 2007-08-30
Oh!! Thank you very much!!! what I was looking for was the Control+Shift+N and the shift+insert! I'm going to install vim, but I must use vi because I have a teacher that order us to use it on the programming exams! :). Thanks again!

---

### Post by asmoore82 on 2007-08-30
> **fredscripts said:**
> Oh!! Thank you very much!!! what I was looking for was the Control+Shift+N and the shift+insert! I'm going to install vim, but I must use vi because I have a teacher that order us to use it on the programming exams! :). Thanks again!

unless you are working on a stone-age UNIX machine, vim and vi are the same thing** ...
I was just letting you know that Ubuntu definitely does not come with the full version of vi/vim
that supports syntax highlighting and other such advanced features, and that the
real full version of vi is just 1 simple apt-get away :D!

**running 'vi' with no filename to edit will show you the vim welcome screen

---

### Post by fredscripts on 2007-08-30
Ok!! Thanks for the advise, I'll do it :)

---

### Post by Nekiruhs on 2007-08-30
> **reckless2k2 said:**
> vi isn't friendly for that copy feature you are looking for. i don't think you can do that with nano either. that might be only for a gui based editor like gedit or kedit. 

as far as keyboard shortcuts, that's in the kcontrol menu you can bind keys to start programs. if you have konsole open, hitting alt keys navigating is what you are looking for. i think that's what you talking about.
You can do it in nano.

---

