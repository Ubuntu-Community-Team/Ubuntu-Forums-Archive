---
title: "I'm confused by these /.* directories, help!"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by therenee on 2006-12-30
I have looked around the forums here and the ubuntu guide and can't seem to find the answer to this. I have a feeling it's probably been answered before and is really simple, so I apologize for being such a total beginner. 
My question is what is with the directories that start with a period? :confused:  Is there any way to get to them in the GUI? What are they for? I was just reading some forum posts and I've seen this before, such as /.icons. I've also seen the period before the slash, like ./flashplayer-installer - is this the same sort of thing, or completely different? Thanks in advance for the help!

---

### Post by capitalistpiglet on 2006-12-30
Theres no mistery to them they are just hidden files, if you dont want to see them then in konqueror go to view > then untick show hidden files. It should be somthing similar in nautilus as well.

---

### Post by taurus on 2006-12-30
The . means current directory so **./flashplayer-installer** means run **flashplayer-installer** from the current directory.  On the other hand, two dots, .., means previous directory...

---

### Post by zek725 on 2006-12-30
these /.* directories contain the important files such as configuration files that you do not want to mess with. if you really want to have it viewable, you can hit Ctrl+H to display the hidden files or copy it then save it without the . prefix.

---

### Post by DavidW2 on 2006-12-30
If you are using Ubuntu and want to view the hidden files in Nautilus, just check 'Show Hidden Files' under the View menu or press Ctrl+H.

---

### Post by atomic0x on 2006-12-30
When you see a period before a forward slash that indicates the current directory.  So when you type ./flashplayer-installer the shell will execute the flashplayer-installer program from the current directory if it exists.

Hidden (ie .gnome/) directories are there mainly to store personal settings.  I don't find many occasions when I need to change anything in them, but you can enable hidden files in your file manager to view them.

---

### Post by macogw on 2006-12-30
> **atomic0x said:**
> Hidden (ie .gnome/) directories are there mainly to store personal settings.  I don't find many occasions when I need to change anything in them, but you can enable hidden files in your file manager to view them.
~/.vimrc is a good one to play with though, that's how you get syntax highlighting in vim.

---

### Post by therenee on 2007-01-03
Wow, thanks so much for all the replies everyone! They really answered my questions! :KS

---

