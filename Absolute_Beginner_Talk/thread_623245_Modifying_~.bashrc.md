---
title: "Modifying ~/.bashrc"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-11-25
Hi All

I'm getting sick of typing certain long commands (gksu firestarter, etc.) so I was looking at modifying my bashrc file with some aliases so I can type firewall and firestarter opens. Is this the right thing to do? Am I likely to do any damage? Can anyone provide an example or two so I can see the format?

Thanks for the help,

P.S. If I do modify bashrc will it take effect in the run window (xfrun) or only in the terminal?

P.P.S. I would assume there would be huge conflicts if I added an alias named the same as an existing command? I.E. If I were to make an alias firefox=gksu firestarter. Is there any way to make sure this doesn't happen?

---

### Post by Deathmoon on 2007-11-25
Should be fine to do, just test the command first.  In my .bashrc file I've added the following at the very end of the file:


> # aptitude aliases
alias agac='sudo aptitude autoclean'
alias agc='sudo aptitude clean'
alias agd='sudo aptitude dist-upgrade'
alias agi='sudo aptitude install'
alias agr='sudo aptitude remove'
alias agu='sudo aptitude update'
alias sug='sudo gedit'

Also, if you like to have right-click funtionality check out [http://g-scripts.sourceforge.net](http://g-scripts.sourceforge.net)

---

### Post by High Camp on 2007-11-25
Thanks much Deathmoon.

I figured as much but my test system is dead at the moment (hence it is a test system) so I have to do this on the live system.

Thanks for the examples and link as well. I'm on Xfce, which uses Thunar, so I don't think a lot of those Nautilus scripts will work for me but I may rewrite them for Thunar.

Thanks,

---

### Post by nick_h on 2007-11-25
You may also be interested in reading [this](http://ubuntuforums.org/showthread.php?t=616875) thread in Community Cafe.

---

### Post by jorges00 on 2007-11-25
Here's a tip in another direction:
 
Uncomment these two lines in /etc/inputrc (or maybe create a local version at ~/.inputrc):
> # alternate mappings for "page up" and "page down" to search the history
"\e[5~": history-search-backward
"\e[6~": history-search-forward
Now start tiping a command and press PgUp or PgDn to look for the same pattern in your command history. I can't live without  this. In fact I just started w/ ubuntu (I used Gentoo a lot) and I was going crazy  until I found how to "fix" the default behavior in ubuntu.

I hope this is  usefull.

jorges

---

### Post by nick_h on 2007-11-25
Thanks, this is useful.  Someone else was asking about this recently but I can't find the thread.

---

### Post by Deathmoon on 2007-11-26
In regards to the history portion, it's a great feature but it's very bad (IMHO)...the history will catch your root password and it will store it in clear text, etc.

[http://gentoo-wiki.com/SECURITY_Adjusting_The_Way_Bash_History_Funtions](http://gentoo-wiki.com/SECURITY_Adjusting_The_Way_Bash_History_Funtions)

Just a FYI...

---

### Post by bapoumba on 2007-11-26
Another tip for commands you use often, hit <ctrl><r> at a prompt, and then enter a couple letters from the command. That's what I use ;)
For ex:
```
(reverse-i-search)`pre': gnome-network-preferences
(reverse-i-search)`rest': sudo /etc/init.d/networking restart

```

The downside is that you have to find specific letters.

---

