---
title: "shift + backspace"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-03
When i press and hold those two buttons, something happens. Try it yourself.
It seems that gnome session is terminated and i jump back to console.

When i'm typing stuff in terminal, it happens that i press those buttons. Can i switch this thing off ?

---

### Post by BarfBag on 2007-01-03
You either jumped into a virtual terminal or killed your X.  These shortcuts are so useful, why would you want to get rid of them?  :confused:

---

### Post by meng on 2007-01-03
Classic example of how to help yourself using the forum's search feature:
There are lots of threads with the words "shift" and "backspace" in the title, most of these appear to be solved threads: here's one of them
[http://www.ubuntuforums.org/showthread.php?t=186714](http://www.ubuntuforums.org/showthread.php?t=186714)

---

### Post by thomasa93 on 2007-01-03
I agree that it can be a useful shortcut, but to disable that and many more, go to:  System-->Preferences-->Keyboard Shortcuts

---

### Post by Sasa_Ivanovic on 2007-01-03
> **thomasa93 said:**
> I agree that it can be a useful shortcut, but to disable that and many more, go to:  System-->Preferences-->Keyboard Shortcuts
you're wrong there's no shift+backspace shortcut there!

---

### Post by meng on 2007-01-03
Check out my post I believe this is an xgl/beryl issue.

---

### Post by Sasa_Ivanovic on 2007-01-03
i need to do this :
```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```
but how can i add this script to the start-up.

---

### Post by Sasa_Ivanovic on 2007-01-03
> **meng said:**
> Check out my post I believe this is an xgl/beryl issue.
nah, it isn't. I ran normal GNOME session. without running beryl-manager.
still there's the problem.

---

### Post by meng on 2007-01-03
Save as a script, go to System > Pref > Sessions and add it there.
EDIT: well if it isn't related to xgl, I'm not sure what's going on, that was a commonly reported issue. Perhaps your forums search will find another thread that is relevant to your problem.

---

### Post by Sasa_Ivanovic on 2007-01-03
ok, thanks!

---

### Post by Sasa_Ivanovic on 2007-01-03
it doesn't work...
when i type the command in terminal and execute it, it works.
i created a file named no_shift+space.sh, added the command to it, saved it.
then i went to System > Pref > Sessions and add it there. But it seems that this script isn't executed...
am i missing something?

---

### Post by meng on 2007-01-03
Is the file executable?
ls -l no_shift+space.sh
(obviously you have to be in the same directory as the file)

if not, 
chmod a+x no_shift+space.sh

---

### Post by Sasa_Ivanovic on 2007-01-03
changed the mode, still nothing. It's not executed at all.
i verified this by adding a dummy command.

---

### Post by meng on 2007-01-03
Do you have a 
#!/bin/sh
as the first line?
(not sure if it's necessary but it can't hurt)

---

### Post by MkfIbK7a on 2007-01-03
If you put terminal programs to startup, they will execute. It's just that they wont show a new terminal. Try to put this to startup in pref sessions:


gnome-terminal -x your_command

I hope it works.

---

### Post by Sasa_Ivanovic on 2007-01-03
nope, i'm gonna add it and restart ... 
i'll see what happens.

---

### Post by Sasa_Ivanovic on 2007-01-03
still won't execute.
is there another way than adding a start-up program to sys > pref > sessions ?

---

### Post by MkfIbK7a on 2007-01-03
there is a "startup folder"
/.config/autostart.
perhaps look through this thread 
[http://www.ubuntuforums.org/showthread.php?t=330472](http://www.ubuntuforums.org/showthread.php?t=330472)

---

### Post by meng on 2007-01-03
Okay have you tried other solutions? You can test them out by running as a one-off command first before using it as a startup script.
[http://www.ubuntuforums.org/showthread.php?t=280872](http://www.ubuntuforums.org/showthread.php?t=280872)
You would be better off doing the search yourself and looking through the various options. Good luck.

---

### Post by Sasa_Ivanovic on 2007-01-03
i figured out, that this script does execute, but not right away.
I have to wait about 5 minutes to see the script executing...
it's really frustating, is there a reason for this ?

---

### Post by Sasa_Ivanovic on 2007-01-03
i solved it!
I added the command in the "startberyl.sh" script, and i added it before the call to the beryl-manager.
This was the first idea i had just that i added the command after, so it hasn't worked.

thanks everyone, for the feedback!

---

### Post by meng on 2007-01-03
> **Sasa_Ivanovic said:**
> i solved it!
I added the command in the "startberyl.sh" script, and i added it before the call to the beryl-manager. This was the first idea i had just that i added the command after, so it hasn't worked. thanks everyone, for the feedback!
Right and here I was thinking the problem was not beryl-related ... but it clearly was. Never mind, glad it worked for you.

---

### Post by Sasa_Ivanovic on 2007-01-03
Damn beryl it just brings me trouble... but i can't stop using it, it's like drugs!

---

