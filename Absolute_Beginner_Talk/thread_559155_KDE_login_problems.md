---
title: "KDE login problems"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by mathemagician on 2007-09-24
Ok,

I'm relatively new to linux, and I've been running Kubuntu 7.04 for the last 6 months or so. Here's what happened:

I got dangerously close to filling my system drive. As soon as a noticed, I backed up and deleted about 20gb of data. 

Upon reboot, I couldn't log in. I'd type my password, and it would just bring me back to the login screen.

So I dug around in failsafe mode and found that the 20gb of data that I thought I deleted hadn't actually been deleted (even though the KDE trash bin was empty and my drive showed 20gb of space).

So I manually deleted the data in the terminal, df -h showed 18g free.

Then on reboot, I was stuck on a black screen with an "x" cursor.

I hit Ctrl-Alt-F1, tried:

sudo dpkg-reconfigure xserver-xorg

Now when I login, I still get a black screen with the 'x' cursor, but a functioning Konsole terminal window appears in the upper left corner.

I managed to login once, I'm not sure how or why.

Help?

---

### Post by mathemagician on 2007-09-24
I can get to the KDE desktop by choosing "console login" at the login screen, logging in, and then using the "startx" command.


If I try logging in normally from the login screen I just get a Konsole window.

Any ideas?

---

### Post by Pumalite on 2007-09-24
Have you tried reinstalling the KDE Desktop?

---

### Post by aysiu on 2007-09-24
What happens when you create a new test user and log in with the test user? Same problem?

---

### Post by mathemagician on 2007-09-25
Thanks for the suggestions.

I made a test user account. 

No problem there.

So, is there anyway to fix my old user account, or do I need to delete it and start from scratch? (something I rather wouldn't do)

---

### Post by aysiu on 2007-09-25
> **mathemagician said:**
> Thanks for the suggestions.

I made a test user account. 

No problem there.

So, is there anyway to fix my old user account, or do I need to delete it and start from scratch? (something I rather wouldn't do)
I would just start fresh and copy over the important config files from the old user account.

---

### Post by mathemagician on 2007-09-25
Remind me again which ones are the important ones.

:)

---

