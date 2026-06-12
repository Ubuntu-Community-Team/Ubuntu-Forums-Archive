---
title: "[SOLVED] Include a password with a terminal command line"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-16
Hi there. I'm wondering if it is possible to include a password with a command line entered into the terminal with sudo.

For example, if I were to type 'sudo gedit' I would then be asked for my password, however, is there a way to do this: 'sudo <password> gedit', so that I do not need to enter my password after I press return to execute the command?

---

### Post by milosz.galazka on 2008-01-16
Hello,

It would be very insecure. Just look at *history* command.
You could write small script using *expect* but please don't do this.

---

### Post by seventhc on 2008-01-16
I'm not sure if that is possible, but if it is, it definitly isn't secure.
First your password would show in plain text
second, it would be recorded in your .bash_history
Since you still have to enter your password, why not just do it in the normal way?

---

### Post by kellemes on 2008-01-16
You better configure /etc/sudoers to your needs.. You can set all kind of goodies in there, including the amount of time you'll have root-priviliges.
As I remember it's set at 5 minutes by default on Ubuntu? Well, set it a little higher..
And you can always use su.


man sudoers
man visudo
man sudo

---

### Post by MaxVK on 2008-01-16
The command line in question will never be seen 'in the open' because it will be executed from within a compiled program. You would click a button, the command line would be created internally, and if you have supplied the program settings with your password, that would be added to the command line before the program executed it. No terminal window would ever be seen.

---

### Post by p_quarles on 2008-01-16
> **MaxVK said:**
> The command line in question will never be seen 'in the open' because it will be executed from within a compiled program. You would click a button, the command line would be created internally, and if you have supplied the program settings with your password, that would be added to the command line before the program executed it. No terminal window would ever be seen.
You mean that the compiled program calls the bash command? If that's what you mean, it would still show up in your .bash-history file. 

The better idea here is to run the compiled program using sudo. If nothing else, a process that gives root access (even if its "invisible") to a non-root user is just asking for trouble.

---

### Post by MaxVK on 2008-01-16
> You mean that the compiled program calls the bash command? If that's what you mean, it would still show up in your .bash-history file.

Ah now! I didn't know that! So if I were to call 'sudo <password> gedit' from within the program, that line would still show up in the bash history? Is there some way to prevent that?

Failing that I would have to try and work out some way for the program to determine if it has been called with gksudo.

Thanks all. I learn something new every day!

---

