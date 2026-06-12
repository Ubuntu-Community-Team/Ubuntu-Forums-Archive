---
title: "desktop shortcut for FAH command"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-03-19
Is it possible (and if so, how) to make a desktop shortcut / launcher to run this command that would otherwise be ran at the terminal as follows:

/foldingathome/CPU1/./qd 

Yes, I have tried and so far, I have not been able to get it to work.  It just gives a fleeting display of the terminal and then goes back to the desktop.

Is the something similar to a PAUSE command in DOS ?

Thanks.

---

### Post by bwingbob on 2007-03-19
> Is it possible (and if so, how) to make a desktop shortcut / launcher to run this command that would otherwise be ran at the terminal as follows:

/foldingathome/CPU1/./qd 

I assume you are using gnome, can't tell from your profile.

[INDENT][LIST=1]
[*]Right click on your desktop.
[*]Select Create Launcher.
[*]In the drop down box at the top of the dialog, select Application in terminal
[*]Give the launcher a name.
[*]Browse the the executable you want to run
[/LIST][/INDENT]
> Is the something similar to a PAUSE command in DOS ?

Try sleep.

[B]sleep NUMBER[SUFFIX]...
  or:  sleep OPTION
Pause for NUMBER seconds.  SUFFIX may be `s' for seconds (the default),
`m' for minutes, `h' for hours or `d' for days.  Unlike most implementations
that require NUMBER be an integer, here NUMBER may be an arbitrary floating
point number.

      --help     display this help and exit
      --version  output version information and exit
[/B]
Hope this helps.

---

### Post by wpshooter on 2007-03-19
Is sleep command placed immediatly after the command to be run, i.e. on the same line ?

What is syntax of [suffix] ?   Is this [s,10] for a pause of 10 seconds ?  or just [s10] ?

Thanks.

---

### Post by bwingbob on 2007-03-19
```
sleep 10s
``` will cause your script to wait 10 seconds.

```
info sleep
``` will tell you more than you ever wanted to know about the sleep command.

Good Luck.

---

### Post by wpshooter on 2007-03-19
When I put this as command it still does not pause.

home/wpshooter/foldingathome/CPU1/./qd sleep 10s

---

