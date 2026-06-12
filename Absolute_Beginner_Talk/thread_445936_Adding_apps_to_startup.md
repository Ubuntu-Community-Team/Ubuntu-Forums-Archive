---
title: "Adding apps to startup"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-16
I am new to ubuntu and linux, but am impressed so far. Even considering switching all my vista and xp boxes to linux. That being said, I have a question in regards to loading applications on startup. I have succesfully downloaded avant and screenlets and would like them to start after signing in. I have tried to do this through system -> sessions, but have had no luck. Can someone please walk a newbie through the process. Adding screenletsd start in the command line did not work for me for screenlets and I tried browsing for avant in the file manager but am use to looking for .exe. Thanks

---

### Post by Najand on 2007-05-16
Open Sessions.
Then click on "new".
Then type Name: "screenletsd"
Then type Command: "screenlets-tray"
click Ok and close sessions, then restart X by Ctrl + Alt + BackSpace.

---

### Post by mejy on 2007-05-16
As a general rule, to find the command to start an app type the following in a terminal:
'cat '
then drag the shortcut into the terminal window.  Then type ' | grep "Exec" '.

Press enter and the output you get will be 'Exec=' followed by the path to the executable.  You should be able to copy this part of the output into the session dialogue.

---

### Post by jputman01 on 2007-05-16
you should be able to just add it to system->prefs->sessions choose start up progams and add

avant-window-navigator

is that how you did it before?

---

### Post by jba6511 on 2007-05-16
> **Najand said:**
> Open Sessions.
Then click on "new".
Then type Name: "screenletsd"
Then type Command: "screenlets-tray"
click Ok and close sessions, then restart X by Ctrl + Alt + BackSpace.

Did this and for some reason it did not work. Followed your instructions. Do I need to go into current session tab and save the current session? After entering the command, clicking ok, and closing I then restarted but upon restart the daemon did not load up.

---

### Post by jba6511 on 2007-05-16
> **jputman01 said:**
> you should be able to just add it to system->prefs->sessions choose start up progams and add

avant-window-navigator

is that how you did it before?

I have an avant-window-navigator folder, but could not find a file with that name. Sorry guys, newbie struggling.

---

### Post by jba6511 on 2007-05-16
> **mejy said:**
> As a general rule, to find the command to start an app type the following in a terminal:
'cat '
then drag the shortcut into the terminal window.  Then type ' | grep "Exec" '.

Press enter and the output you get will be 'Exec=' followed by the path to the executable.  You should be able to copy this part of the output into the session dialogue.

got this:
blake@ubuntu:~$ cat 
'/usr/local/share/applications/avant-window-navigator.desktop' '| grep "Exec"'
'/usr/local/share/applications/avant-window-navigator.desktop' '| grep "Exec"'

What am I doing wrong?

---

### Post by jba6511 on 2007-05-16
finally got screenlets working on startup. The instructions to add screenlets-tray were correct, something was messed up with my permissions where it would not save the changes made to startup. Now I just need to figure out how to get avant to load. Thanks for the help so far guys.

---

### Post by jba6511 on 2007-05-16
any ideas on avant

---

### Post by jba6511 on 2007-05-17
well I figured it out, was easier than expected. For those who need to know, just type avant-window-navigator in the command line in the start up programs.

---

