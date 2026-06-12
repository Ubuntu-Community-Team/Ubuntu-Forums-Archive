---
title: "Monitoring computers at work"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by jasonray_f on 2005-07-27
My work wants to migrate to Linux from Windows. We use SpectorSoft Pro ([www.spectorsoft.com](www.spectorsoft.com)) to monitor employee computer usage.

Is there a comparable app for Linux, or any other solutions that could do the similar?

---

### Post by mad_scientist03 on 2005-07-27
What information, specifically, are you trying to log about each user?

---

### Post by jasonray_f on 2005-07-27
+Web sites visited
+Applications used
+Blocking of web messengers (like the 'java' versions of Yahoo, MSN Messenger, etc)
+Periodic screenshots
+Keystroke recording
+Email recording (for evlotution)

---

### Post by sonny on 2005-07-27
[QUOTE=jasonray_f]+Web sites visited
+Applications used
+Blocking of web messengers (like the 'java' versions of Yahoo, MSN Messenger, etc)
+Periodic screenshots
+Keystroke recording
+Email recording (for evlotution)[/QUOTE]
Wow... it seems that in your company the employee trust is unheard of.  [-X 

Well for the blocking web messenger you just have to avoid installing them, and take the user acount off the root group, that way they won't be able to use sudo, therefore won't be able to install anything, wich you can also do to avoid improper applications to be use, if that's what you meant.

---

### Post by mad_scientist03 on 2005-07-27
That's quite a comprehensive list. I can't think of a single application off the top of my head that would accomplish all of those tasks.

sonny lists a couple of things you can do. You can also limit the number of web browsers installed to one (say, Firefox) and have a script set up in a cron job that combs through the browser cache and history to see what's been viewed. 

You could also use the gimp to take screenshots, though I'm not sure what the state of performing this action from the command line is.

---

### Post by sonny on 2005-07-27
here are some keyloggers:
[http://www.freedownloadscenter.com/Best/keylogger-linux.html](http://www.freedownloadscenter.com/Best/keylogger-linux.html)

You can also write some scripts to take the screenshot or to review the browser cache, I don't think that using gimp for the screenshots would be good, but you can use ksnapshot (if you are using KDE) or the thumbviewer in gnome, but my guess is that you'll have to write down some scripts.

---

### Post by mad_scientist03 on 2005-07-28
I think you're right; my suggestion to use the gimp is not a good idea, especially if there are smaller, more command-line friendly tools available.

---

