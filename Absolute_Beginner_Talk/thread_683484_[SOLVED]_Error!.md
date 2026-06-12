---
title: "[SOLVED] Error!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-31
Hello!
What can I do?
```
hooman@hooman-laptop:~$ apt-get update && apt-get install frozen-bubble
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```
Thanks!

---

### Post by Ainab on 2008-01-31
sudo apt-get update && apt-get install frozen-bubble

only root user can update and install packages so every time you want to install program use sudo

---

### Post by p_quarles on 2008-01-31
That error occurs when you have more than one instance of the package management utility open. Make sure that Add/Remove Programs and Synaptic are closed, then try again.

---

### Post by Hoom@n on 2008-01-31
Really thank you! But what is this sudu and susu which I used them alot?!
+++
Yea, I'm running updattes at this time. I try after update again. (before starting update it was like now too, so I think that sudu should work. But I'll try with and without sudu after the updates)
___
Thanks

---

### Post by oedha on 2008-01-31
have you turn Add/Remove or synaptic or update manager or software source OFF ?
they must turn OFF

~E~

---

### Post by p_quarles on 2008-01-31
I haven't heard of "susu," but "sudo" allows you to run a function which requires root privileges on your machine. It will ask for your password when you invoke it.

---

### Post by Hoom@n on 2008-01-31
Thanks alot for the help.
+++
everything worked!
___
Thanks again!

---

### Post by p_quarles on 2008-01-31
Glad you resolved the problem. 

I noticed that you have a lot of posts. You can help other users with similar questions by marking these threads as "solved" when a solution is found. To do this, click on the "thread tools" button at the top of the page. Thanks.

---

### Post by Hoom@n on 2008-01-31
OK I gonna do that, thanks to tell it.

---

