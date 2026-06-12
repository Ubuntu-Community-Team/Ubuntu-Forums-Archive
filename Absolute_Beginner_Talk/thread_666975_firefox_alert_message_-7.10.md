---
title: "firefox alert message -7.10"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by The Cheat on 2008-01-13
I just restarted my computer and now im getting this alert when i try and open firefox (it no longer opens and im using a different browser) 
> Could not initialize thebrowsers security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recomended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features.

i haven't changed anyfiles for firefox so i'm not sure why this started happening...

---

### Post by wesley_of_course on 2008-01-13
Welcome to Ubuntu !    Have you tried reinstalling Firefox ? Not sure but 
it might fix whats wrong . What version of it are you running ? Did you import any settings ?
 when you set it up ?

---

### Post by The Cheat on 2008-01-13
yea i went into package manager and reinstalled... no change ..
the firefox is the default for 7.10 and i did add some extensions to it but it was working fine with all of them before the re-boot. 
and i set up the system 2 days ago

and wow .. very fast reply!:-D

---

### Post by kenno69 on 2008-01-30
I have identical problem...need help please.
p.s installed epipher and thats works ok.
ta
ken

---

### Post by Joeb454 on 2008-01-30
Please read post #2 and post back if you did anything mentioned in that post :)

---

### Post by kenno69 on 2008-01-30
Done reinstall ..nothing apart from stumbler has been added. Has been working ok for 8 weeks. Frustrating but Epiphany working well.
Seems to be a security issue.
Kenno

---

### Post by shae on 2008-01-30
Close firefox and run the following.

```
mv ~/.mozilla/*/bookmarks.html ~/Desktop/bookmarks.html && rm -r ~/.mozilla
```

That backs up your bookmarks to your desktop and deletes your firefox profile.  Then open firefox and restore your bookmarks.

---

### Post by kenno69 on 2008-01-30
No still no go..

---

### Post by bomanizer on 2008-02-19
I've got this issue also. I've recently tried other WM's besides gnome, so the reason could be somewhere on that line... anyway, I've tried all these:

remove & reinstall firefox
remove with the --purge option & reinstall
remove .mozilla -folder
deleted my profile & created a new one

It doesn't help.

EDIT:

I went as far as removing /etc/firefox

Also, this issue is system-wide, it affects all users, including root.

---

### Post by Sinkingships7 on 2008-02-19
> **The Cheat said:**
> yea i went into package manager and reinstalled... no change ..
the firefox is the default for 7.10 and i did add some extensions to it but it was working fine with all of them before the re-boot. 
and i set up the system 2 days ago

and wow .. very fast reply!:-D

did you by any chance try to install the addon "allpeers"?

---

