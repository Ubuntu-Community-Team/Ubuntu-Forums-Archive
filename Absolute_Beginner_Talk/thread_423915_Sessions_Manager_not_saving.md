---
title: "Sessions Manager not saving?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by mikedpirone on 2007-04-26
Hi everyone I am a new Linux convert from Windows XP. I switched to Ubuntu Fiesty this week because frankly I was sick of having to use cracked programs and Ubuntu offers me everything I do on Windows but for FREE. Now I have everything pretty much up and running the way I want except for one thing that has been bugging me and I can't figure it out. I want Check Gmal app to run at start up so I add it to the sessions manager. Sessions Manager will not save anything I want it to launch at startup though. It doesn't matter what it is. I add it then go back to sessions manager and its not there. Anyone have any clue as to what is going on or a little work around that I can use to launch stuff at start up? :confused:  Thanks in advance

---

### Post by AmyRose on 2007-04-26
If I remember correctly, if you go to System --> Preferences --> Session or something like that, you should be able to set a list of things to start when you log in. That is, if you're using Ubuntu.

If you're in Kubuntu, you just go to ~/.kde/Autostart in Konqueror and drag the menu entries into that window.

---

### Post by orb9220 on 2007-04-26
Gnome

System>preferences>sessions

On Startup Progams click on new. 

1) Now make sure you also give the command in the command box and not just the name box.

Example: Name: Check Gmail
  ..               Command: checkgmail
Click Ok
Now click on sessions tab and make sure Automatically save changes is checked,

Now logout then log back in.

---

### Post by mikedpirone on 2007-04-26
I was doing everything except the last step of checking off automatically save changes. That might have been the problem. I will check when I get home and see how it goes.

---

### Post by mikedpirone on 2007-04-26
I just tried that and it is still not saving the sessions. I have seen other people post about this problem. Is there any other way to add stuff to startup?

---

### Post by leashy on 2007-04-27
Bump. Same for me. It will not save it no matter what. Even though i have the box checked to automatically save. I can edit an entry that is already there such as "Update Notifier" by unchecking the box for it to start up, but when i open the startup manager, it is re-checked. Any solutions anyone?

EDIT: Found Fix
[URL="http://ubuntuforums.org/showthread.php?t=286883"]
http://ubuntuforums.org/showthread.php?t=286883[/URL]

---

