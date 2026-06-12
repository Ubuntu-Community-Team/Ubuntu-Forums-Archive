---
title: "What's the difference between Terminal and Bash?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by dogen on 2007-09-19
What's the difference between a terminal program like Konsole or Gnome terminal and Bash? Is there a command to tell which shell the terminal is running?

thanks.

---

### Post by jordanmthomas on 2007-09-19
The terminals like gnome-terminal and konsole are called virtual terminal emulators.
They pretend they are a real linux console (see CTRL - ALT - F1 (F7 gets you back) ).

When you log in to a terminal / virtual terminal, your shell is run.  This *can* be any executable on the entire system (or on another system, I'd imagine).  In Ubuntu and most other distros, the default shell (program run on login) is bash.  You can see what shell you are using by fingering yourself.  :lolflag:

for example, I finger myself
```
[FONT="Courier New"]&#9484;&#9472;(jordan@ttyfscker:pts/2)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(00:32:%)&#9472;&#9472; finger $USER                                                     &#9472;&#9472;(Wed,Sep19)&#9472;&#9496;
Login: jordan                           Name: Jordan Thomas
Directory: /home/jordan                 [COLOR="Red"]Shell: /bin/zsh[/COLOR]
Office: Jobe 318,                       Home Phone:
On since Tue Sep 18 02:38 (CDT) on vc/1 (messages off)
No mail.
No Plan.[/FONT]

```

This will show you a user's shell.  If you want to try a new shell, you should try it out first by simply running it from within bash.  When you've found a shell you like, you can change it permanently by doing this:
```
chsh -s /bin/zsh jordan 
```
Replace /bin/zsh with a shell of your choice and jordan with your own user name.


Hopefully I've clarified what a shell is a little bit.
```
shells:
    zsh, bash, csh, etc
terminals:
    urxvt, gnome-terminal, xterm, konsole, etc.

```
Your terminal executes your shell, more or less.

---

### Post by kellemes on 2007-09-19
Very helpful answer, thanks jordanmthomas.

---

