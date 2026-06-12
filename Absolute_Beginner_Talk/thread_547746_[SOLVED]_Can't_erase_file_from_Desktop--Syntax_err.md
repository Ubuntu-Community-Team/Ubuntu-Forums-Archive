---
title: "[SOLVED] Can't erase file from Desktop--Syntax error due to (2) being in file name"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by MrPerfecto on 2007-09-10
Hello all.  I'm new to Linux and Ubuntu so please bear with me.  This question pertains to Feisty Fawn 7.04.  In the process of installing a binary file (Java if I remember correctly), I ended up with a jre-6u2-linux-i585(2).bin on my Desktop.  I've tried to remove this file using recovery console and terminal,  but the remove process ends with a syntax error stating the the "(" character is unexpected, ... it's called an unexpected token if I remember correctly.  I've tried to delete the file, rename the file, etc., and everything fails because of the syntax error.  Any suggestions?

---

### Post by swisscow on 2007-09-10
try from the terminal ```
rm *.bin
``` when you are in the desktop folder. Don't know if it will work but you never know

---

### Post by rsambuca on 2007-09-10
Just be cautious when using the rm command with the '*' wildcard, as it can do some major damage!  You should be OK in your Desktop folder, though.

---

### Post by MrPerfecto on 2007-09-10
Thanks everyone!  That was fast!  (I've only been working on this all day yesterday before deciding to send my first post.)

The wild card worked.  I entered "sudo rm *.bin" and poof...it was gone!  Thanks again!

---

### Post by swisscow on 2007-09-10
Excellent!

---

### Post by Beggar on 2007-09-10
The answer posted, even though it works, is incorrect. It will delete all the bin files in the directory, not just the one you want to remove. For future reference, when you come across a character like this the command you should run is 

```

rm jre-6u2-linux-i585\(2\).bin

```

the slashes will "escape" the parenthesis so that the terminal knows that it is just a part of the name, In the future, after you start typing the name of the file, if you press the tab button it will autocomplete the filename, including adding any escape characters that are needed.

---

