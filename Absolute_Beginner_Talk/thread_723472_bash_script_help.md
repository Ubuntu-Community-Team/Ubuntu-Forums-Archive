---
title: "bash script help"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by prol on 2008-03-13
What command will make a window popup saying "Done".
Thanks in advance:)

---

### Post by handydan918 on 2008-03-13
Any command you want to use after you write the program that constitutes the window.

AFAIK, bash is not what you want to use to manipulate windows...
If you just want to send the user some information at the terminal, you can tell the shell to output any text you like with "echo".
For example, cut and paste the following line into a terminal window:

echo "I wish you knew how to write code." 

What exactly are you trying to do?

---

### Post by prol on 2008-03-13
I'm encoding videos using ffmpeg and converting the  files using nautilus scripts.The problem is that it runs in the background.

---

### Post by scorp123 on 2008-03-13
> **prol said:**
> What command will make a window popup saying "Done".
Thanks in advance:) ```
xmessage "Done"
``` ... For more details check the manual: ```
man xmessage
```

---

### Post by bodhi.zazen on 2008-03-13
Check out zenity :

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by forrestcupp on 2008-03-13
> **scorp123 said:**
> ```
xmessage "Done"
``` ... For more details check the manual: ```
man xmessage
```

Sweet.  You learn something new every day.

---

### Post by prol on 2008-03-13
One more thing:
how can I force a bash script to run in a terminal

---

### Post by handydan918 on 2008-03-14
Not sure what the issue is. Could you rephrase that? 
The script has to be made executable...is that what you mean?

---

### Post by prol on 2008-03-14
no I meantto force a bash script to always  run in a terminal window and not in background.

---

### Post by glennric on 2008-03-14
If you execute a script from a terminal, it will run in a terminal unless you append and ampersand to the end of the line.  Do you mean, how do you make a script that is run from another script or cron or something run in the foreground?  Perhaps this is what you are looking for...
```
x-terminal-emulator -e script-name
```

---

### Post by prol on 2008-03-14
Thanks you guys for all your help.Open source is great

---

### Post by hyper_ch on 2008-03-14
/me thinks popups are eveil ^^

---

