---
title: "How do you scroll up and down in CLI?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by æþeling on 2006-03-22
I really need to know how to scroll up/down in a command-line enviroment (like when you press alt+ctrl+F1, not in gnome terminal), please reply if you know:mrgreen:

---

### Post by localzuk on 2006-03-22
Have you tried 'Shift + PgUP/PgDown'? This is what I use normally...

---

### Post by æþeling on 2006-03-22
that only works in a virtual terminal (gnome terminal/konsole/xfce4terminal/xterm)

---

### Post by Brunellus on 2006-03-22
If you have a lot of output from a command, you should pipe the command to the "less" program, which will allow you to scroll through the output line-by-line.  When you're done, you hit "q" to quit (yes, "less" is its own little program)

so, for instance, say you wanted to look at your system log, which lives at /var/log/syslog

ordinarily, you'd just

cat /var/log/syslog

and that would print the contents of the file.  of course, the syslog is LONG, so it would scroll for ages, without your being able to stop it.  if you wanted to go through it line by line, you can always

cat /var/log/syslog | less

(that's a vertical bar, or "pipe" between "/var/log/syslog/" and "less").  The pipe turns the output of cat (the print of syslog) to the input of less, the input of less then becomes a scrollable thing that you see before you.  Page through with the vim keys, or the arrow keys.  spacebar goes down a full page.)

Alternatively, you can save the results of any command by redirecting that command's output to a file using a > character, so

cat /var/log/syslog >/home/brunellus/examplefile

would print all of syslog and redirect that output to a new file in my home directory called "examplefile."  You can then open up that file in your favorite text editor (vim, emacs, nano, vile, or whatever)


Generally, the shell is great because you can string little programs together with pipes, redirections, and links to come up with novel and interesting ways of solving problems/answering questions.

---

### Post by kabus on 2006-03-22
> that only works in a virtual terminal (gnome terminal/konsole/xfce4terminal/xterm)

Works on the console too here. Maybe there's something wrong with your keyboard settings ?
As an alternative you could run screen, which will not only give you working scrolling (Ctrl-a, Esc, then use the cursor keys) but also cut and paste.
Here's some tutorials :
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

---

### Post by localzuk on 2006-03-22
I don't believe that is correct - I will check it now :) Maybe it is not what I am remembering... (Not at an ubuntu comp at the moment)

---

### Post by ubuntuuser on 2006-03-22
[QUOTE=æþeling]that only works in a virtual terminal (gnome terminal/konsole/xfce4terminal/xterm)[/QUOTE]
Actually, that does also work on the terminal that you access over the Ctrl+Alt+Fx combination, I just tried it.

---

### Post by localzuk on 2006-03-22
Nope, it definitely works on my ubuntu box here. Shift+PgUp/PgDown

However it only stores a limited buffer of the information (I don't know the actual amount) so you don't get to see everything that has been on your terminal.

You may wish to look into a program called 'screen' which allows for greater control over matters such as buffer length IIRC.

Also, if you simply wish to scroll through recently entered commands, you just need to use the arrow keys (Up/Down).

---

