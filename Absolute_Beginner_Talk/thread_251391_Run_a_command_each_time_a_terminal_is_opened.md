---
title: "Run a command each time a terminal is opened?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by m0nstr42 on 2006-09-05
I'm embarrassed to have to ask this, but how, from the command line, could I go about opening a new terminal, executing a command in that terminal, and leaving the terminal open?  Doing ```
gnome-terminal -x my-script
``` *almost* works, but it closes the terminal as soon as the command is done.  Same with gnome-terminal -e my-script (I don't even see what the difference is?).

---

### Post by tatimmer on 2006-09-05
try putting a space and then the ampersand & at the end.

---

### Post by m0nstr42 on 2006-09-05
Tried that.  That only gives you back the first terminal; the new one still dies after it executes the script.

---

### Post by tatimmer on 2006-09-05
Here is a workaround, though its probably not what you intended.  For the last two lines of your script:

echo Hit Enter key to continue:
read  stor

---

### Post by m0nstr42 on 2006-09-05
Yeah, that's more of a workaround.  There's gotta be a real way to do this.  The end result I really want is to have the terminal there and waiting with a prompt.

---

### Post by drummer on 2006-09-05
put the script you want to run in ~/.bashrc then it should run when you open up bash.

---

### Post by jISh on 2006-09-05
Or you could put bash in the beginning of your script. 
When it finishes, you'll be inside a child bash process. If you type exit you will be returned to the original bash, and if you typed exit again the gnome-terminal would close.

---

### Post by m0nstr42 on 2006-09-05
I don't want to put it in .bashrc because I don't want it to run every time I call up bash.

I could add bash to the beginning of the script, but that still seems like a bit of a work around.

Isn't there a way to pass a command to a terminal to run when it is open and have the terminal proceed as normal afterwords?  Is it such a screwy thing to want to do that there isn't a proper way to do it?

---

### Post by 23meg on 2006-12-19
In the "Title and Command" tab of your gnome-terminal profile, choose "Hold the terminal open" in the "When command exits" combo box. Or append "read" to the script you use to launch your app.

---

