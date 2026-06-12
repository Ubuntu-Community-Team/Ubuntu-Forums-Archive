---
title: "question about my keyboard"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-26
Hey guys, 

I realize there are countless threads posted about this problem but i could not find one to fit my certain problem.

I am using a dell inspiron laptop keyboard and i am having problems with some of my characters.

First of all let me say that all of the Alphabet letters (A-Z) work perfectly.  Where im having te most problem is when i need to write a quotation mark ( " )  I have to press the key twice consecutively, and even when it prints the character, it is a much smaller set of quotation marks that are almost unrecognizable.

I did the right thing and went in to my preferences menu and made sure that i had the correct keyboard selected (whatever the default American keyboard is) and it was already selected and chosen as my default.

Any suggestions?

---

### Post by ITdrummer on 2007-07-26
And one more smaller issue:

When using firefox or IE on my windows machine, i use Alt + [left] and Alt + [right] to navigate back and forward, respectively, on my web browser.  I cannot seem to get this to work in firefox using Ubuntu.  

I searched around in the firefox settings menu and once again in ubuntu's keyboard menu and i cannot find anything partaining to this.

As i said, this is a small issue, but i would love to be able to navigate without using my mouse.

---

### Post by wolfen69 on 2007-07-26
open terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
skip the video and mouse setup if there are no problems. it might help.

---

### Post by ITdrummer on 2007-07-26
what does that line of code do?

---

### Post by Orochi on 2007-07-26
> **ITdrummer said:**
> what does that line of code do?

It's a gui for reconfiguring your xserver settings, which (among many other things) control your keyboard layout. When it gets to the part where it asks for your keyboard type, make sure to choose the correct one.

---

### Post by ITdrummer on 2007-07-26
> **Orochi said:**
> It's a gui for reconfiguring your xserver settings, which (among many other things) control your keyboard layout. When it gets to the part where it asks for your keyboard type, make sure to choose the correct one.

well, like i said, when i go to system> preferences > keyboard ......the correct keyboard is already selected.  

Is there a separate keyboard layout for laptop keyboards?

---

### Post by ITdrummer on 2007-07-27
bump

---

### Post by ITdrummer on 2007-07-27
Does the laptop keyboard need to be specified when selecting a keyboard layout?

---

### Post by ITdrummer on 2007-07-30
Hey guys, promlem solved.

When i went in to reconfigure my xorg i noticed that the keyboard layout was 105 and it needed to be 104.  Thanks for everyones help.

---

