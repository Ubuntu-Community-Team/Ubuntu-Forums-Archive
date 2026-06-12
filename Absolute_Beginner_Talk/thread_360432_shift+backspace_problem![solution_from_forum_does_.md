---
title: "shift+backspace problem![solution from forum does not work for me]"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by effi on 2007-02-13
hey there,
i need your help with this problem:
everytime i press shift+backspace my xgl is restarted..
this is really annoying because i often just press these 2 buttons by accident during a long chat/coding session...
-->after restart everything is gone..
i tried fixing this by typing:
xmodmap -e "keycode 22 = BackSpace BackSpace", this seems to get rid of the shortcut problem,

but it doesn't work at my system..
all i get is:
xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'BackSpace”' for reading
xmodmap:  5 errors encountered, aborting.

.. i don't get what this means ...
hopefully you can help me,
thanks
bye effi

---

### Post by effi on 2007-02-13
i really need your help,
this problem sucks!

---

### Post by g3k0 on 2007-02-13
It should be this -

xmodmap -e “keycode 22 = BackSpace BackSpace Terminate_Server”

---

### Post by effi on 2007-02-14
...
thanks but then i get another error:

xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'Terminate_Server”' for reading
xmodmap:  6 errors encountered, aborting.

...?!"

---

### Post by Crooksey on 2007-02-14
```
xmodmap -e \"keycode 22 = BackSpace Delete\"
```

---

### Post by effi on 2007-02-14
nice one ...!!!
finally, i got rid of mx problem!!
thanks alot!!
greetings effi

---

### Post by Crooksey on 2007-02-14
No worries, enjoy!

---

