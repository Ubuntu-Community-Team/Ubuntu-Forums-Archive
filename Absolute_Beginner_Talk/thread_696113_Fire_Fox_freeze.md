---
title: "Fire Fox freeze"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by TMpBG on 2008-02-13
When I try to go to this forum Fire Fox freeze for a some time and go black.This start to happen after I change Edit-->Preferences-->Content-->Load images automatically, Enable JavaScript and Enable Java.I have no problem with other sites.If i undo the changes this forum is normally loaded.
"this forum" =  [http://ubuntuforums.org/](http://ubuntuforums.org/)

Todor

---

### Post by Blutack on 2008-02-13
Could you open a terminal window (Accessories --> Terminal)
and then run firefox from there
(type firefox in and press enter).
Then make it crash and post the output.

---

### Post by nemilar on 2008-02-13
I second this!!!  Every so often going to the Ubuntu Forums will crash Firefox 2 on my computer :( :( :( 

I was going to start a thread to see if was a common problem, but I started using the Firefox 3 beta, and it doesn't happen anymore, so I kind of just ignored it.

---

### Post by TMpBG on 2008-02-13
***
Could you open a terminal window (Accessories --> Terminal)
and then run firefox from there
(type firefox in and press enter).
Then make it crash and post the output.
***

There is no output... I don't think it is really crashing.I forgot to write that after some blackness I can move around the forum with no problem, but if i try to go to [http://ubuntuforums.org](http://ubuntuforums.org) it load slow and go black again and after some time it's ok...until I try to go again to this specific page.

---

### Post by Blutack on 2008-02-13
Weird.
You tried loading FF without any extensions?

---

### Post by TMpBG on 2008-02-13
***
Weird.
You tried loading FF without any extensions?
***

Just tell me what to write in terminal.

I think the problem have to do  something with
Load images automatically, Enable JavaScript and Enable Java.

---

### Post by Blutack on 2008-02-13
> firefox -safe-mode
I use firefox with images, javascript and java and do not have these problems.

---

### Post by TMpBG on 2008-02-13
***
I use firefox with images, javascript and java and do not have these problems.
***

I have this problem when I use fire fox without them.No problem when I use them.:)

---

### Post by imon9 on 2008-02-13
to everyone,

it is known issue that firefox freeze on "java-script" heavy site...and ironically ubuntuforum (which use the script on the link bar on the top of the page....

anyway, good news is firefox3 is not having this problem... dunno why, but most probably a combination of new rendering engine + various bug fix and memory leak fix helps... many extensions are already firefox3 ready....so still dont..but wont hurt to try it...

use the one in synaptic ... (for easier installation :D )

---

### Post by TMpBG on 2008-02-13
Thanks...(now when i know about it it's really *known issue* :popcorn:)

---

