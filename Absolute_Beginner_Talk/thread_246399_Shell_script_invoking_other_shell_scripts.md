---
title: "Shell script invoking other shell scripts?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Freddd on 2006-08-29
I have installed Tomcat and I have these two files:
startup.sh
shutdown.sh

I would like to create my own shell script file called restart.sh and let the invoke shutdown.sh and then startup.sh. This is probably easy, but I would really appreciate help.

---

### Post by Klaidas on 2006-08-29
Restart the PC, or an application?

---

### Post by Freddd on 2006-08-29
Restart Apache Tomcat Application

Is it this easy?
sh startup
sh shutdown

And put this in my own shell script file?

---

### Post by Freddd on 2006-08-29
Hmm doesn't seem so...

---

### Post by Tomosaur on 2006-08-29
When you invoke a Bash script, the **place you invoke it from** is treated as the current directory, and not the place the script resides. For that reason, you should always give filenames an actual path. Let's say your startup and shutdown scripts are in /home/me/twoscripts/, and your custom shell script to invoke them is in /usr/bin/.
Your script then, should look something like this:

sh $HOME/twoscripts/startup.sh
sh $HOME/twoscripts/shutdown.sh

Of course, I haven't tested this, so it may not work, but you do have to be careful with filenames and paths when scripting.

---

### Post by Freddd on 2006-08-29
Thankyou very much, it works :)

---

