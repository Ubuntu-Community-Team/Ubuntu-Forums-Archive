---
title: "How can I make &quot;tab&quot; in my shell window autocomplete?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-03
If I have two files on my desktop named "bobby.txt" and "bobtacular.txt", and I just type "b" into the shell window, and then hit "tab", the computer beeps.

I would prefer to make this work more like the command prompt on XP, where when I hit tab, then I can scroll through all possible tokens for the given string...

Anyone know how?

---

### Post by Daveski on 2008-01-03
Press TAB again.

---

### Post by joesmith1234 on 2008-01-03
> **Daveski said:**
> Press TAB again.

Hmm, so if I type "b", this looks like it gives a list of every file starting with a b in the system, then I have to hit enter many times to get to the end of the list, and I am eventually dumped back to the prompt.

I want something that I can just hit a key, and the shell autocompletes to the first possible filename in the current directory... just like the MS command prompt.

---

### Post by Borbus on 2008-01-03
Well it's not going to list bobby.txt or bobtacular.txt because it cannot run those things, try typing gedit followed by b then tab twice, it lists them, type enough to make it unambiguous then tab again. I don't know how to make bash act like windows shell, I'm not sure why you would want to, bash is at least a million times better than the windows shell.

---

### Post by joesmith1234 on 2008-01-03
> **Borbus said:**
> bash is at least a million times better than the windows shell.

Maybe this is personal preference...  it's cumbersome to not have an autocomplete feature... at least I don't know of one.

And the beep is annoying :)

Any suggestions would be graciously accepted.

---

### Post by Borbus on 2008-01-03
The beep is the terminal bell, you can turn off the audible beep in your terminal program preferences (in Gnone terminal you have to edit your current config).

I used autocomplete in bash all the time, it's second nature now. I promise that once you get used to bash you will bet much productive than you ever could be in windows shell.

---

### Post by joesmith1234 on 2008-01-03
> **Borbus said:**
> 
I used autocomplete in bash all the time, it's second nature now. I promise that once you get used to bash you will bet much productive than you ever could be in windows shell.

so what is it?

---

### Post by nick_h on 2008-01-03
The auto-completion should be enabled at the bottom of you .bashrc file by default.  You can check this by typing:
```
cat ~/.bashrc
```

Auto-complete in bash is context sensitive.  It will complete commands, filenames, variables depending on the context.  Type:
```
cat b
```
and then press TAB and it should complete the filename.

It will complete as far as it can go before the completion is ambiguous.  It will then stop and beep.  You are then supposed to add a character (or more then one) and then press TAB again.  If you don't it should beep to warn you.  If you persist and press TAB again you will get a list of choices unless the list would be large.  For large lists you will be asked if you want to continue or not.

---

### Post by scottmuz on 2008-01-03
zsh has completion turned on by default and its competion is
superior to bash.

To use zsh do:
sudo apt-get install zsh
chsh -s /usr/bin/zsh

---

### Post by creperum on 2008-02-05
> **nick_h said:**
> 
Auto-complete in bash is context sensitive.  It will complete commands, filenames, variables depending on the context.  

Okay, I have a question about context-sensitive completion.  I had two machines running Ubuntu, both I think running Feisty.  On my home machine, tab-completion works as you describe: commands, filenames, which is exactly what I expected.

On my office machine, though, it surprised me: if I had a bunch of files with different extensions, it would pick the one that fit the program I was using.  For example, if I had paper.tex, paper.aux, paper.dvi, paper.log in a directory, and I type "xdvi pap [TAB]", it will choose "paper.dvi".

I didn't tweak anything on my office box, just installed Ubuntu off the CD and went from there, so where did this behaviour come from?  More importantly, how can I get in on my home machine? Is this some sort of tab-completion feature that I can turn on?

---

