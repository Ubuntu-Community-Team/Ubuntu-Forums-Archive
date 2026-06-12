---
title: "Vim is driving me crazy."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by JetSirus on 2007-05-30
Okay, perhaps I'm stupid, but the friggen help for vim is not working.  Let me see if I am getting this correct.  First you press ":" minus the quotes, then the cursor will move to the bottom of the screen.  Then you can type "help" minus the quotes and it's supposed to take you to the help system.  Is that correct?  If so why does it always give me an error.   
```
E433: No tags file
E149: Sorry, no help for help.txt
```
What the devil?!?!  This is really making me crazy.  I'm gonna give this one more hour then vim can go DIAF.  :p

---

### Post by sankarv on 2007-05-30
theres no problem in that steps. do the help file exists? have u changed any settings for vim.....

it might be the problem with that ...

---

### Post by JetSirus on 2007-05-30
Nothing has changed.  This is a near fresh install of Ubuntu.

---

### Post by userundefine on 2007-05-30
Try installing vim-full.  The standard fare might not include the docs.

sudo apt-get install vim-full

---

### Post by wormser on 2007-05-30
I had issues with vi and the arrow keys.  My fix was to install the full version.  Maybe it will work for you.

```
sudo aptitude install vim-full
```

---

### Post by JetSirus on 2007-06-05
Thanks the issue is now resolved.

---

