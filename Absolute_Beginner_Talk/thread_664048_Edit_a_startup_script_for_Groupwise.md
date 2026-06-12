---
title: "Edit a startup script for Groupwise"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Amanda T on 2008-01-10
I have a really really easy question if someone can take two seconds and help me out!

I have a problem with my Groupwise email client and I found the answer through forum searching ([http://ubuntuforums.org/showthread.php?t=504983&highlight=groupwise+grey+screen&page=2](http://ubuntuforums.org/showthread.php?t=504983&highlight=groupwise+grey+screen&page=2)), I need to add *AWT_TOOLKIT=”MToolkit”* to the startup script for the program.

One person who had this work for them quoted the path as /opt/novell/groupwise/client/bin/groupwise, I would assume that mine is the same, is that correct?

So my question is, what command or code do I put into Terminal so that I can add this little thing to the startup script??

Thank you so much in advance, this really is a wonderful community. :)

---

### Post by Blutack on 2008-01-10
> gksu gedit /opt/novell/groupwise/client/bin/groupwise

and then put the 

> AWT_TOOLKIT=&#8221;MToolkit&#8221;

bit before anything else but after all the comments (blue hashy bits)

---

### Post by Amanda T on 2008-01-10
Thank you so much for the help. It looks like that wasn't the fix that I needed. :( I'm going to give it another go, make sure I pasted everything right and so on, and if that doesn't work I'm back to the drawing board.

Thanks!

---

### Post by Blutack on 2008-01-10
This seems to be the same fix as I use with matlab.  The thread is here:
[http://ubuntuforums.org/showthread.php?t=467133&highlight=matlab](http://ubuntuforums.org/showthread.php?t=467133&highlight=matlab)

---

### Post by Amanda T on 2008-01-10
I guess I just had the insert in the wrong spot, because when I moved it over a bit it worked just fine!!! Thanks again!!!!!

---

### Post by Blutack on 2008-01-10
No worries!

---

