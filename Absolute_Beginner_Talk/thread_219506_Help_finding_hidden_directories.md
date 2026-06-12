---
title: "Help finding hidden directories"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-07-20
I'm currently using amule and its saving the incoming files to a hidden directory in my home folder. When I use the file browser to search for it I get nothing, not even when I click the box "Show hidden files and folders" under preferences.

There's like 50 hidden directories in my home folder, how can I view them?

---

### Post by crystal on 2006-07-20
What if you just click View -> Show Hidden Files in the file browser?

---

### Post by risbac on 2006-07-20
> There's like 50 hidden directories in my home folder, how can I view them?

CTRL+H in Nautilus should display them. If not, you have a bug somewhere... 

The setting you tried is probably not applicable for folders, only to files.

---

### Post by UberIcarus on 2006-07-20
I've allready done that, still nothing. Amule can see all the hidden folders, but I can't (and neither can the search function) through GUI interface. Even when I click show hidden files and folders.

---

### Post by UberIcarus on 2006-07-20
thanks risbac, I'll try that.

---

### Post by crystal on 2006-07-20
hmm... okay, what if you go to the command line and (when in your home directory) type:
ls -a

---

### Post by UberIcarus on 2006-07-20
Ooooohhhkaaayy...evidentally I needed to reboot before it would show me the hidden directories. Problem solved.

---

### Post by risbac on 2006-07-20
Cool, enjoy!

I still don't understand why amule places files in a hidden directory... I would not set it this way. Anyway...

---

