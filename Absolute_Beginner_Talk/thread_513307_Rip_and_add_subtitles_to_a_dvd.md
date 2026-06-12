---
title: "Rip and add subtitles to a dvd?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by DonBucknall on 2007-07-30
Hello,

Is there a way to rip dvd's and add new subtitles to the dvd and burn it?
I bought a dvd box when I was on holiday but now I want to rip them and add dutch subtitles.
The important thing is, the subtitles should be visible via dvd player on tv and that they are synced.

If this is possible, is there a way to modify the menu?

Thanks,

Don

---

### Post by Pragmatist on 2007-07-31
[https://help.ubuntu.com/community/DVD::Rip](https://help.ubuntu.com/community/DVD::Rip)

---

### Post by DonBucknall on 2007-07-31
Thanks for your reply,

But if I rip subtitles, I need to translate them(thats not a problem) or download them(also not a problem.) but how do I put them back on the dvd, synced and everything.

Thanks,

Don

---

### Post by Acglaphotis on 2007-07-31
Try DeVeDe for de-ripping. Its AWESOME!.

---

### Post by DonBucknall on 2007-08-05
I need to place the subtitles back not only rip them... :P

Does someone know?

thanks,

Don

---

### Post by Pragmatist on 2007-08-05
Apparently DeVeDe CAN add your own subtitles:
[http://blogcritics.org/archives/2007/02/05/150718.php](http://blogcritics.org/archives/2007/02/05/150718.php)

Read the Comments section of the above page:

> hey man hoy are you, do you know how to put subtitles, i allready download the subtitles but i dont know how to put them in the dvd, do you know how?

>  
1.- open devede
2.- select video dvd
3.- add files (your movie) it opens file properties select your movies and open option advance in the section Misc, write the next sentence in the textbox extra parameters for mencoder :

-sub /home/subtitulo.srt -subcp enca:es:latin1 

where /home/subtitulo.srt is your subtitle.

---

### Post by DonBucknall on 2007-08-06
Thanks, I'll read about it and try it. If it worked I'll post it here.

Thanks for help,

Don

---

### Post by izhitzza on 2008-03-03
You can also try this program here: uglysub.com -- it has some bugs, but it works more or less. Or you can insert the subtitles by hand using spumux (comes with dvdauthor) to insert the subtitles into an MPEG file, then author that using dvdauthor... that's it really.

Good luck.

---

