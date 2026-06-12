---
title: "New to ubuntu(and all operating systems other than windows)"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Magictv on 2008-02-15
Hi there, I installed ubuntu about 30 mins ago.  It was pretty easy to do but i managed to overwrite everything else on the hard disk, rofl i'm an idiot.  If there's a way to fix that i'd be happy but I doubt there is and i don't mind too much anyway.

Anyway I have a problem with my sound.

The computer I have installed this on is a dell inspiron 9400.  And it's impossible for me to stop it making sounds.  I have muted it and turned the volume fully down, however when I am in pidgen messenger and hold backspace down it makes a loud beeping noise.  Also, it plays a little tune when it starts up.

If anyone knows of how to solve this I'd be very grateful.

Thanks for reading.

---

### Post by SOULRiDER on 2008-02-15
The beep is normla i think, try clicking the pidgin tray icon and click on Mute Sounds. In the preferences menu you should be able to disable sounds too.

---

### Post by kesman on 2008-02-15
For sounds, first right-click on the volume on the top right corner, and open up volume control. Mute all of those, and if this doesn't work, go to Applications -> Accessories -> Terminal and type in it:
```

alsamixer

```

and press Tab to view all channels. Then browse trough them and mute every one by pressing M. Then exit with ESC.

Enjoy your silent ubuntu :)

---

### Post by phr0ze on 2008-02-15
You can put the drive as a second drive in another windows machine and try a piece of software called R-Studio. It can handle drives that have moved from one format to another. It wont recover the OS or anything, but it will let you get your files out.

You can try R-studio before you buy. You will get to see the list of files it can recover.

[http://www.r-studio.com/](http://www.r-studio.com/)

It will cost you $50 if you need to buy the software. But if it's going to work, it's worth it.

EDIT: Be sure you download the regular R-Studio demo. Not the emergency or agent demos. They are for a different purpose.

---

### Post by stevejesus on 2008-02-15
Wow...  Now I can become a computer forensic scientist!

---

### Post by Anicka on 2008-02-15
I think that the sound you hear is a so called system beep. It is a noise saying "hey, now you did something that I don't understand or don't like. Do something about it!". By going in the menu system -> preferences -> sound and choose the third tab, you can change the setting for system beeps.

---

### Post by Magictv on 2008-02-15
Thanks for the tips guys and yes it was the system bleep.

I will try the r-studio program as well.

Thanks again for the fast help :)

---

