---
title: "How can I create a &quot;launcher&quot; (or &quot;shortcut&quot;) on the &quot;Applications&quot; Menu?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-17
Hello all !!!

I managed to install a program called: "gambas".

Unfortunately the program does NOT create automatically a "launcher" inside my Ubuntu's "Applications"  Menu.

To run the Program, I need to do the following:

1. Press "Alt+F2"

2. Type "gambas"

Then the program launches...

How can I create a "launcher" or "shortcut" & put it inside my Ubuntu's "Applications" Menu?

Thanks.

P.S.> I have tried the following:

1. From the Menu, select "Applications\Add Applications"

2. On the window named "Add Applications" that pops up, on the left hand side, I expand the list under "Programming".

3. I scroll down & also expand the list under "More Programs..."

4. In that list I locate & select "Gambas"

Now I am stuck!!!

The program is ALREADY selected - HOW am I supposed to ADD it if it is ALREADY added....?


Please Help...

---

### Post by meborc on 2006-03-17
[https://wiki.ubuntu.com/HowToAddaLauncher](https://wiki.ubuntu.com/HowToAddaLauncher)

hope this helps :) ... wiki - the best documentation about ubuntu

---

### Post by dvarsam on 2006-03-17
I saw the site you suggested.

But, I want to put this launcher INSIDE my Ubuntu "Applications" Menu.

I do NOT want it lying loose on My Desktop....

Any ideas on this?

Thanks.

---

### Post by mcduck on 2006-03-17
[QUOTE=dvarsam]I saw the site you suggested.

But, I want to put this launcher INSIDE my Ubuntu "Applications" Menu.

I do NOT want it lying loose on My Desktop....

Any ideas on this?

Thanks.[/QUOTE]
It's been a while since I booted my Breezy install, but you should have a menu editor somewhere in Application menu. If you don't install 'smeg' (short for simple menu editor for gnome). If you can't find it, try to look for 'alacarte', as that is what it's called in Dapper. Or just do a synaptic search for 'menu editor' :)

---

### Post by Brunellus on 2006-03-17
use the menu editor or open terminal and type 

smeg

that'll get you the menu editor, to which you can add a launcher using substantially the same method.

---

### Post by Christmas on 2006-03-17
I'm also a newbie to Linux but I think I can help you with this. For my shortcuts, I used this way: Applications -> System Tools -> Applications Menu Editor. Once there, just click on New Entry than add the path to your program (i think it should be in /usr/bin). From that point you can also add custom submenus to your Application menu. Hope this helps you.

LE: Now I see Brunellus said exactly the same thing, I didn't know what "smeg" does anyway.

---

### Post by aysiu on 2006-03-17
Applications > System Tools > Applications Menu Editor

---

### Post by chuckyp on 2006-03-17
If you want to find the path to the program just open a terminal and type "which gambas" or whatever the name of it is.  That will show the path the binarary.

---

### Post by dvarsam on 2006-03-20
Quote:
The program is ALREADY selected - HOW am I supposed to ADD it if it is ALREADY added....?


_I found the solution to this_:

Since the Shortcut already existed inside the "Applications\System Tools\Applications Menu Editor", but did NOT show under Ubuntu's "Applications" Menu...
...inside the "Applications\System Tools\Applications Menu Editor" I created a SECOND shortcut pointing to the SAME program.

ONLY then did it show up inside my Ubuntu's "Applications" Menu.

Thank you all guys!!!

---

