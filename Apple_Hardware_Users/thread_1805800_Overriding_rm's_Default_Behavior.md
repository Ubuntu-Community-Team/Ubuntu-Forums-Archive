---
title: "Overriding rm's Default Behavior"
date: 2011-07-16
forum: Apple Hardware Users
---

### Post by FreshSocksFiend on 2011-07-16
Within the last few weeks, I've been beginning to familiarize myself with Terminal. I know within the syntax, you can add options such as [FONT="Courier New"]-i[/FONT] or[FONT="Courier New"] -v[/FONT].

When I enter the command[FONT="Courier New"] rm[/FONT], I want Terminal to automatically go interactive (which would be the [FONT="Courier New"]-i[/FONT] option) without me having to add it to the command. Meaning, I'd rather type [FONT="Courier New"]rm Test.doc[/FONT] than having to include [FONT="Courier New"]-i[/FONT] like this [FONT="Courier New"]rm -i Test.doc[/FONT]. This way, whenever I execute the [FONT="Courier New"]rm[/FONT] command, I won't have to worry about adding the [FONT="Courier New"]-i[/FONT] option because I know that Terminal will automatically ask me if I want to delete the file or not before I do.

I hope that question wasn't too confusing, that I worded it clearly. If so, I can clarify. Thanks :)

---

### Post by 1clue on 2011-07-16
alias rm='/bin/rm -i'

Try that in the terminal, and if you get the behavior you want then add it to your $HOME/.profile somewhere near the end.

---

### Post by FreshSocksFiend on 2011-07-16
It worked! Thanks so much 1clue :)

---

### Post by FreshSocksFiend on 2011-07-16
> **1clue said:**
> 
add it to your $HOME/.profile somewhere near the end.

Oh wait, how do I do that?

---

### Post by 1clue on 2011-07-16
> **FreshSocksFiend said:**
> Oh wait, how do I do that?

Use your favorite editor to edit the .profile file in your home directory.

I use vim, which based on the little I have seen of your posts you Do Not Want.  Maybe gedit?

---

### Post by FreshSocksFiend on 2011-07-16
Thanks again so much :)

---

