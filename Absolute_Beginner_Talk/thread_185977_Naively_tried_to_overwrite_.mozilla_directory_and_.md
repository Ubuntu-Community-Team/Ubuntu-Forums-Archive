---
title: "Naively tried to overwrite .mozilla directory and broke firefox"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by virtualcourtney on 2006-06-01
Whoops. :)

I'm a Linux newbie; I had a brief (unfruitful) affair with SuSE on my laptop for about a week, and today I installed the new Dapper Drake distro (it dual boots with XP, everything there works just fine).

What I tried to do was to save my .mozilla directory from SuSE on a shared partition between the OS's and overwrite it in Ubuntu.  Now, every time I try to run firefox (even after rebooting), it says it's already running--either to close it or reboot.

Should I just empty out the .mozilla directory and reinstall firefox, or is there some preferred way to keep a profile?

Thanks in advance. :)

---

### Post by Kimm on 2006-06-01
Thats strange... it shouldnt be doing that.

But if your having trubble you should clear it out (no need to reinstall Firefox).

You can save your bookmarks by locating bookmarks.html in your .mozilla folder, and backing it up. Then run Firefox to let it recrate its config files, close it, and add the old bookmarks.html file.

path to bookmarks.html:
"/home/<your username>/.mozilla/firefox/<random>.default"

(Note: Everything inside "<>" shoud be changed to what they describe... just to make sure you know)

PS.
I copied my bookmarks.html to my lapptop so I know this works!

---

### Post by virtualcourtney on 2006-06-01
Thanks!

What I ended up doing was creating a new user (the boy wanted his own login, anyway...) and then copying over the default .mozilla directory from his account.  I had some trouble getting the default profile set up (something to do with firefox not having permission to write to the directory it wanted to), but I ended up just changing the folder and that worked fine.

Now, I'm going to see if I can somehow copy over my extensions...  Your bookmark tip worked perfectly!

(I think the fun is in the breaking of things, anyway!)

---

