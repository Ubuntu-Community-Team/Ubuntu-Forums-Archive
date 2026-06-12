---
title: "[SOLVED] Help! Can't get to login screen!?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by jbryant on 2008-01-13
Please help a Noob out! I was messing around with startup manager and session options and I don't remember what all else, but now when I boot, I get to a window that Reads "No serving hosts were found", with a section at the bottom of the window to add hosts. What is this and how can I get rid of it?  I can't get logged in, so I'm basically screwed until I get past this!  Thanks for any and all help.

---

### Post by amingv on 2008-01-14
Perhaps you set your machine to remote login by accident?

Try searching for a menu, usually at the bottom or the left of that dialog box (Not sure if it's there in Gnome) and select "Local Login". Alt+L also switches you back to local login.

---

### Post by mikeyphi on 2008-01-14
> **jbryant said:**
> Please help a Noob out! I was messing around with startup manager and session options and I don't remember what all else, but now when I boot, I get to a window that Reads "No serving hosts were found", with a section at the bottom of the window to add hosts. What is this and how can I get rid of it?  I can't get logged in, so I'm basically screwed until I get past this!  Thanks for any and all help.

Normally these are setup on Network:
127.0.0.1 localhost
127.0.1.1 yoursystemname.yournetworkdomainname

On the latter you need to give/remember your computer a name
and give/remember your network a name

Hope that all you need to do is enter your info for the 127.0.1.1 address!!!

---

### Post by jbryant on 2008-01-14
Thanks for the ideas, I'll give them a try this evening after work.

---

### Post by jbryant on 2008-01-14
After a little more research, I found the answer in this thread.

[http://ubuntuforums.org/showthread.php?t=617144]("http://ubuntuforums.org/showthread.php?t=617144")

---

