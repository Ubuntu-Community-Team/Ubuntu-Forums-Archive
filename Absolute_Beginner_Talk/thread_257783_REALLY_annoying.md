---
title: "REALLY annoying"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-09-15
Okay, I have some experience with this but I figured this was a beginner question and need some insight on it.

I can NOT for the life of me get things to start on boot. If I add them to the session manager (system->preferences->sessions and on the startup programs tab) when I close the manager, they just go away....poof~!

What is going on here?

---

### Post by redDEADresolve on 2006-09-15
maybe this will help.

when you enter the start up script do you put the file path in?

for compiz to load on start up I have to enter "/usr/bin/compiz-start"

hopefully that helps

---

### Post by Henry Rayker on 2006-09-15
one of the things I'm trying to autostart is checkgmail (another is syndaemon) I have both of them configured to autostart on my 64bit installation, and that works just fine. I added them the exact same way as they appear in that installation, but if I close the manager and re-open, they changes I make don't persist. It's as if the manager is reading one file and writing to another.

---

### Post by Henry Rayker on 2006-09-16
NOTE: A complete reinstall fixed it up, but there has got to be some explaination to this. anyone?

---

### Post by Anduu on 2006-09-16
I am not sure what causes this to happen but it has happened to me...If it happens again I can save you a reinstall ;)

Create a script that will launch the app you desire and be sure to make it excecutable.Test it to be sure it works.Then add a link to the script in your startup programs.It has worked for me without fail.

For whatever reason linking to a script will stay while doing it the "proper" way won't...*shrug*

---

### Post by Henry Rayker on 2006-09-16
well, I had some other things that I didn't feel like fixing, so a reinstall was just fine.

It's just silly that it won't link properly, after some time. I did everything I did on the last install (like I believe I said, I had just actually done the install a day or two ago) but to no avail. I couldn't duplicate this behavior...although I didn't install the kernel update. I'll do that and see how it treats me.

---

