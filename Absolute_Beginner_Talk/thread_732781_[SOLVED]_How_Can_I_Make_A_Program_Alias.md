---
title: "[SOLVED] How Can I Make A Program Alias?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-23
Is there a way to create an alias for the terminal that will save me some typing when I start a program?  I'd like to create an alias for the command   hellanzb  .   

I've tried this:     alias hellanzb='h'       and then pressed Enter.

I then tried the command    h     and Enter, but it came back as  

bash: h: command not found

Is there a way to do what I want, and have the system remember it from now on?

Thanks.

FwF

---

### Post by banewman on 2008-03-23
There is a hidden file in you're home folder called .bashrc. Open your home folder in nautilus, click view - then click show hidden files from the top menu - open .bashrc - scroll to the bottom and add your alias with the other system ones.
:)

---

### Post by Oldsoldier2003 on 2008-03-23
> **FreewareFan said:**
> Is there a way to create an alias for the terminal that will save me some typing when I start a program?  I'd like to create an alias for the command   hellanzb  .   

I've tried this:     alias hellanzb='h'       and then pressed Enter.

I then tried the command    h     and Enter, but it came back as  

bash: h: command not found

Is there a way to do what I want, and have the system remember it from now on?

Thanks.

FwF
edit .bash_aliases

format = alias <alaisname>='<command>'  *no space after the = and the ' are required*

```
alias clearth='find ~/.thumbnails -type f -atime +7 -exec rm {} \;'
```

---

### Post by taavikko on 2008-03-23
Edit file ~/.bashrc
> #if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

remove the comments, save and exit
create .bash_aliases file
```
nano .bash_aliases
```
and enter the aliases there, after adding aliases, update bash
```
bash
```

---

### Post by Oldsoldier2003 on 2008-03-23
bashrc comes default in Ubuntu to point to the .bash_alias , I think its a much more elegant solution than hacking lines onto the end of the .bashrc

---

### Post by Joeb454 on 2008-03-23
A sample line from my ~/.bash_aliases
```
alias server='ssh joe@myServerName'
alias kate='/usr/bin/kate'

```

etc. :)

---

### Post by FreewareFan on 2008-03-23
Firstly, a big Thank You to all in this thread!!

I actually only gave an official Thank You to Joeb454  for one reason, and one reason only.   

You see, I followed all the instructions in this thread, and it was just not working...  I was racking my brain trying to see what I had done wrong, cause normally I can follow directions pretty good...  I checked, and re-checked my work, but still it wouldn't work for me...

Then when Joeb454 made that final post, with examples, I found my mistake..  If you will all go back and read my original post, the mistake is right there, glaring at all of us, but no one pointed it out to me...   lol

When I was entering the alias command, I had the <alias_name> and <command>  all bas-ackwards!      I was entering alias hellanzb='h'  instead of the correct way of  alias h='hellanzb'      

That was what was driving me nuts for a bit there....

So, anyways, many many thanks to ALL in this thread!!

FwF

---

