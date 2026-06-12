---
title: "Clearing History"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-07-19
Could someone please tell me how to clear the history of the commands I've typed into the terminal?  I tried emptying .bash_history of text, but the sneaky "history" command still revealed all!  :(

---

### Post by Rocket2DMn on 2007-07-19
You might have to close out the terminal first, then the history can go away.  I'm not at my box to test that though.

---

### Post by Darklighter137 on 2007-07-19
Your suggestion helped a little--now it only shows the last 30 commands for so.

Nevermind:  by repeating the action, it's all gone.  Thanks!

---

### Post by asmoore82 on 2007-07-19
delete the file $HOME/.bash_history and logout of the term

if you would like the history to be cleared every time you logout, add the action to your bash logout hook like so...

```

~$ echo '/bin/rm -f $HOME/.bash_history' >> $HOME/.bash_logout

```

-OR-

```
~$ echo 'true > $HOME/.bash_history' >> $HOME/.bash_logout
``` :D

---

### Post by Rocket2DMn on 2007-07-19
For future reference you can empty a file by loading /dev/null into it.
```
cat /dev/null > filename
```

---

### Post by asmoore82 on 2007-07-19
for future reference the '>' output redirector is slightly dangerous in that it *always* wipes out the previous contents of a file

ergo, the cleanest method of emptying a file would be that redirector in combination with a do-nothing shell builtin command ...
```
~$ echo > *your_now_empty_file*
```
- OR even better still -
```
~$ true > *your_now_empty_file*
```

---

### Post by steve.horsley on 2007-07-19
This command:
**history -c** 
seems to do the trick. Use
**man bash**
and go to line 2627 for more details.

---

