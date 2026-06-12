---
title: "Launcher"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by amontix on 2007-07-25
I have a problem with a launcher.

From the terminal I give the command and the application starts properly.

When I create a launcher from the desktop (right click on the desktop) and I put in the command line exactly the same path command as above the application does not start.

Any suggestions on how to fix it?

Best

Andrea

---

### Post by tomcheng76 on 2007-07-25
what is the command?
post here

---

### Post by amontix on 2007-07-25
From the terminal I write 

/usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run and the application works fine

but if I put exactly the same path in the field command in the launcher nothing happens!

Thanks!!!

---

### Post by tomcheng76 on 2007-07-25
may be you try to change the command in launcher from
/usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run to
"/usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run"

---

### Post by amontix on 2007-07-25
Thanks, but it is still not working!

It appears the terminal but immediately disappears...

---

### Post by trent dillman on 2007-07-25
...

---

### Post by amontix on 2007-07-25
Thank you very much!

Unfortunately, if I type gnome-terminal -e /usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run my application does not start!

Thanks again

---

### Post by amontix on 2007-07-25
In the icon launcher "basic" properties I have:

Type: desktop configuration file
Size 190 bytes
Location /home/andrea/Desktop
MIME type: application/x-destop

"Perimission" : read and write

How can I fix it please?

---

### Post by amontix on 2007-07-27
I hve figure it out the problem.

If I type in the terminal /usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run the apllication works fine.

If I type in the launcher /usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run the apllication immediately crashes...

What could be the problem?


Best

M

---

### Post by tomcheng76 on 2007-07-27
may be you can write a scipt
```

#!/bin/bash
/usr/local/lib/ox-4.00/packages/tsmod4/tsmod_run
```
save it as tsmodscript and put it to your home folder

then make a launcher to the command is ~/tsmodscript

---

### Post by mcduck on 2007-07-27
So that's a CLI application? Remeber to set the launcher to run in a terminal. Otherwise it will run, but you won't see anything happening..

---

### Post by amontix on 2007-07-27
Thanks to everyone!

I have solved with the last tomcheng76 suggestion!

Thanks again!

---

