---
title: "Is it safe to delete keyring?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by muddler on 2008-01-21
I have three keyrings. When I go to Keyring Manager and click on each, I have two options: New keyring and Delete keyring. Is it safe to delete and add new keyring or should I add a new one and then delete? As I am not sure of the passwords of all of them, will I be able to delete? I made enough mistakes for the time being and don't want to add to my list.Thanks for your help.

---

### Post by kryth on 2008-01-21
Someone should come along with a better answer than me. But I know I've royally messed stuff up by messing with the keyring thing. But I can screw up anything to do with Ubuntu. Hope someone gives you a better answer than 'Be Careful"

---

### Post by Golem XIV on 2008-01-21
I think that the keyring manager saves information in the .gnupg folder, so you may want to make a copy of it just in case before you go deleting stuff... :-)

---

### Post by nikoPSK on 2008-01-21
I wouldn't delete... :|

---

### Post by muddler on 2008-01-21
Thanks, but I couldn't find a gnupg folder? Did I not look in the right place?

---

### Post by Golem XIV on 2008-01-21
It's in your home folder.  Note the "." in front, it means it's a hidden folder.  Use Ctrl-h in Nautilus (or "Show hidden files" in the View menu) to see it.

Note that I am not sure if there are any other places where keyrings may be/are stored...

---

### Post by Sinkingships7 on 2008-01-21
there's nothing in my keyring manager, so i can't see how they'd be important unless you know what they're for. but that's just me: you'd probably be better off listening to the other people on this forum, as i can assure you that they're much smarter than i. :lolflag:

---

### Post by muddler on 2008-01-21
When I try ..../.gnupg -h I get the error message: Couldn't find ..../.gnupg -h

---

### Post by nikoPSK on 2008-01-21
just press control H and look for g. :)

---

### Post by fatality_uk on 2008-01-21
Why do you want to delete a keyring, just out of interest?

---

### Post by seventhc on 2008-01-21
you can also open a terminal and put this in
```
sudo nautilus .gnupg
```
Then you will see whats in that folder.

---

### Post by nikoPSK on 2008-01-21
if you ever need to find something just use the locate parameter. :)

ex:
```
locate something
```

---

### Post by kyphi on 2008-01-22
You will find your keyrings in your home folder.  Use Ctrl+h to show the hidden folders and scroll to '.gnome2', open that file and then find 'keyrings'.

I cannot advise you whether or not it is safe to delete since I do not know what you have in those files.

Before deleting, it is best to save the file to another location so that you can put it back if you need to do so.

---

### Post by muddler on 2008-01-23
When I go to keyring I'm asked for the password for default. I do not know and have never known what the password is or where to find it.

---

### Post by nikoPSK on 2008-01-23
> **muddler said:**
> When I go to keyring I'm asked for the password for default. I do not know and have never known what the password is or where to find it.
 
your login password... or your public gpg password?

---

