---
title: "Editing .php files"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-07-12
So, I do a lot of my web work in .php files. When I double-click on .php files, though, I get this message:

[i]The filename "whatever.php" indicates that this file is of type "PHP script". The contents of the file indicate that the file is of type "HTML page". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML page", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/i]

Um, I don't want to change the extension. It's supposed to be .php. And I can open with, but that's a little extra step. Is there any way I can double-click to open the file? Is there a workaround?

---

### Post by sapo on 2005-07-12
Right click on the file -> Properties -> Open With

And there you can chose an editor like gedit or Add another one  :grin:

---

### Post by aysiu on 2005-07-12
gedit is already the default application to "open with." I still get that message. Any tried-and-true solutions?

---

### Post by musicman2059 on 2005-07-12
I work with PHP files myself, too. (albeit only a very small part of that is PHP coding... the rest is HTML :p)  I've found that by using an HTML editor such as bluefish will alleviate the problem. ;)

---

### Post by aysiu on 2005-07-12
Is bluefish in the repositories? Okay. I might start investigator HTML programs, instead of using Gedit. Thanks.

---

### Post by musicman2059 on 2005-07-12
There's a few HTML editors in the repositories, Bluefish and Screem being two of them.

For some strange reason, though, I remember opening a PHP file just fine in gedit.

---

### Post by aysiu on 2005-07-12
[QUOTE=musicman2059]There's a few HTML editors in the repositories, Bluefish and Screem being two of them.

For some strange reason, though, I remember opening a PHP file just fine in gedit.[/QUOTE] No, it *does* open fine with Gedit. I just have to right-click on the file and go to "open with Gedit." If I double-click the file, that's when I get the error message.

---

### Post by pataphysician on 2005-07-12
my non-executable php files open with my text editor, jedit, when i double-click them. executable scripts ask me if i want to run the file or "display its contents" (the latter option opens jedit). in any case, i think you can set the files to open with whatever you'd like: if you right-click a php file and chose the "open with" tab, if it's not already selected, click "text editor" and close the dialouge. then double-click the file and it should open in gedit.

---

### Post by aysiu on 2005-07-12
No, it doesn't, at least not for me. I'm going to give bluefish a try, though.

Hm. Even when I make bluefish the default "open with" application, I still get the message. Is it a Nautilus thing? Is there somewhere else where I set preferences about .php files?

---

### Post by David A Knight on 2005-07-14
Yes, it is a feature of nautilus and will occur whatever application you assign.  It will only occur with some php files that appear to be html by looking at the first few characters.

---

