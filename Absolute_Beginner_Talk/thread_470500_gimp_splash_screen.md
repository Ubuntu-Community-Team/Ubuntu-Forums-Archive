---
title: "gimp splash screen"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-11
how do i change my splash screen for gimp?

---

### Post by HotShotDJ on 2007-06-11
[Google]("http://www.google.com") search term "gimp splash screen" (without quotes) returned [THIS]("THIS") (and several other) hits.  Enjoy.

---

### Post by thesonisshining on 2007-06-11
> **HotShotDJ said:**
> [Google]("http://www.google.com") search term "gimp splash screen" (without quotes) returned [THIS]("THIS") (and several other) hits.  Enjoy.

well............that was helpful. thanks a bunch. :(

---

### Post by HotShotDJ on 2007-06-11
Why the sad face.  The link is there for you to follow and enjoy.  Did you want me to read it for you and repost the entire article here?

---

### Post by thesonisshining on 2007-06-11
this was the link you gave me "http://this/" it's well.... not a very effective link.

---

### Post by HotShotDJ on 2007-06-11
> **thesonisshining said:**
> this was the link you gave me "http://this/" it's well.... not a very effective link.ACK!!  That isn't at ALL what I intended to post!  [http://www.gimp.org/about/splash](http://www.gimp.org/about/splash)  <--- THAT is what I meant to post.  Sorry about that.  NOW can I have a happy face??  ;)

---

### Post by Cilionelle on 2007-06-11
What he/she meant was [http://www.google.com.au/search?hl=en&q=Gimp+splash+screen&btnG=Google+Search&meta=](http://www.google.com.au/search?hl=en&q=Gimp+splash+screen&btnG=Google+Search&meta=).

Edit: Oh, you did it...

---

### Post by thesonisshining on 2007-06-11
:D*there you go*

well i had found that page but i'm a noob and i'm missing something in the instructions. 
where is this located?

> $PREFIX/gimp/2.0/images/gimp_splash.png

---

### Post by thesonisshining on 2007-06-11
ok i found it.....thank you both for your help though.

btw you wouldn't possibly know how to fix this ([http://ubuntuforums.org/showthread.php?t=469925&highlight=gimp](http://ubuntuforums.org/showthread.php?t=469925&highlight=gimp)) problem would you?

---

### Post by thesonisshining on 2007-06-11
so now i found the page folder and file but it won't let me paste the new image in that folder.
what do i do now?

---

### Post by HotShotDJ on 2007-06-11
Try saving the image as /home/$USER/.gimp-2.2/gimp-splash.png (where $USER = your user name)

---

### Post by thesonisshining on 2007-06-11
i tried and this is what i got.
> The name "/home/christopher/.gimp-2.2/gimp-splash.png" is not valid because it contains the character "/". Please use a different name.

---

### Post by HotShotDJ on 2007-06-11
What application are you using to create and save the image? The program is interpreting the entire path as the filename. You'll have to browse to the folder using the "save as" file browser... and probably manually type in the path (everything except "gimp-splash.png") because it is a hidden directory --  and then you can save the file without entering the entire path..

---

### Post by thesonisshining on 2007-06-11
> **HotShotDJ said:**
> What application are you using to create and save the image? The program is interpreting the entire path as the filename. You'll have to browse to the folder using the "save as" file browser... and probably manually type in the path (everything except "gimp-splash.png") because it is a hidden directory --  and then you can save the file without entering the entire path..

i was using nautilus (i believe) since it was already at my fingertips. but here is what i just got when i tried through gimp.
> Saving '/usr/share/gimp/2.0/images/gimp-splash.png' failed:

Permission denied

---

### Post by HotShotDJ on 2007-06-11
Yes... thats because /usr/share ... is read-only for regular users.  You have to be root to write to that directory.  Using Gimp, try saving it to /home/christopher/.gimp-2.2/gimp-splash.png

---

### Post by thesonisshining on 2007-06-11
SWEET!

thank you it's working now. thank you for enduring through my lack of knowledge in this area.

---

### Post by HotShotDJ on 2007-06-11
Cool.  Could you go ahead and edit your original post's topic with [Resolved]?  That will help other users searching the forum with similar questions.

---

