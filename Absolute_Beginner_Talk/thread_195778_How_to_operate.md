---
title: "How to operate?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by traveler.in.time on 2006-06-13
Hey everyone, 
I am a little confused.
I just installed Ubuntu, but I don't get a desktop screen, all I see is something like a Dos prompt.
I don't know any of the commands, although I am trying to maneuver myself through the info sections.  Still it is slow going.
Is there something that I am missing?  
How do I find something that will look a little more familiar to Windows raised youth?

---

### Post by jimcooncat on 2006-06-13
Perhaps you did a server install?

If so, you should be able to get the desktop applications by:

[INDENT]sudo apt-get update
sudo apt-get ubuntu-desktop[/INDENT]

Be prepared for some long downloads.

---

### Post by taurus on 2006-06-13
Sounds to me like you have installed the server version instead of the desktop version!!!  If you want to have window manager like Gnome, then from the prompt, type
```

sudo apt-get install ubuntu-desktop

```
Otherwise, download and install the desktop version of Dapper then...

---

### Post by ajgreeny on 2006-06-13
Just to make sure, type "startx" without quotes at the prompt after logging in as the user you set up at install time.  What error messages, if any do you get?

---

