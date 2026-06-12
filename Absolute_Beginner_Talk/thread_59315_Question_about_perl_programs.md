---
title: "Question about perl programs"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by Watcher on 2005-08-23
I have a very nice perl program written, but in order to make it work really nice it should be run every time I log in (and it should be run in a terminal). Any idea how to do that? (I tried putting it in sessions, but that wont do it).

Thanks in advance.

---

### Post by nad on 2005-08-23
Is there a .bash_profile file in your home directory. I am not at an ubuntu computer at the moment to confirm this, but, this is where you would put commands to be run once upon login. Provided you have permission to run them.

---

### Post by Watcher on 2005-08-23
[QUOTE=nad]Is there a .bash_profile file in your home directory. I am not at an ubuntu computer at the moment to confirm this, but, this is where you would put commands to be run once upon login. Provided you have permission to run them.[/QUOTE]
 Well it's like this, it's a little perl program that checks a database and then displays if there are any birthdays that day or not.

So, ideally it should run at startup (there is a if thing built in, so it only checks every 24 hours). But no idea how to do that (maybe some sort of popup if anyone knows something of perl and how to make that).

Beware I'm totaly new at this soo if you suggest some thing please do in detail :)

---

### Post by nad on 2005-08-23
I'm sorry. You requested the location to run at every terminal login which would be ~/.bashrc .

I am not clear whether you are requesting assistance using the graphical tools or with your test routine.

Perhaps you wish to post your code that the community may help, within your choice of licensing.

---

### Post by Stormy Eyes on 2005-08-23
I used to dabble in Perl, so I might be able to help.

---

### Post by Watcher on 2005-08-23
Perhaps I asked in the wrong way ;)

Ok new try at it then: I have written a program in perl which need to be run at login. I tried using the "run at startup tab" in the system - preferences - session but that won't do (it says it's working but i don't see any terminal).
So how do I get this to run every time I log in (and have it preferably displayed in a terminal window).

---

### Post by stoffe on 2005-08-23
What happens if you set ```
gnome-terminal -x /path/to/program
``` or possibly ```
gnome-terminal -x perl /path/to/program
``` in startup? 

From **gnome-terminal --help**: [FONT=Courier New]
-x, --execute                             Execute the remainder of the command line inside the terminal.[/FONT]

---

### Post by Watcher on 2005-08-24
[QUOTE=stoffe]What happens if you set ```
gnome-terminal -x /path/to/program
``` or possibly ```
gnome-terminal -x perl /path/to/program
``` in startup? 

From **gnome-terminal --help**: [FONT=Courier New]
-x, --execute                             Execute the remainder of the command line inside the terminal.[/FONT][/QUOTE]
That doesn't do the trick, tried it but it just will not show any terminal window.

---

