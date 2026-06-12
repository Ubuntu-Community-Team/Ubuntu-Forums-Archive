---
title: "Can't get Ubuntu Live-CD to fully load... so close!"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Theo-Ubu on 2006-05-01
I'm trying the 5.1 "breezy badger" version Live-CD.  It gets all the way along to the little Ubuntu logo with the progress bar, but then it switches back to text-mode for a a little bit, then it acts like it's going to finally boot into a desktop enviro, but then it just goes to a blank screen and the CD seems to just keep reading forever.

I'm unsure if there's anything I can do to diagnose why it's failing the final steps when it seems so close to finallly booting.  Since the screen goes completely dark/blank, I don't know how to diagnose anything in the absence of even some text output.

Any ideas on what I could try next?

---

### Post by Sef on 2006-05-01
What are you computer specs, especially graphics card?

---

### Post by Theo-Ubu on 2006-05-01
I'm dealing with an older iMac.  It has aprox. 100Mb of RAM, but I'm not sure what the specs are on the video output or card, as it's kind of integrated into the motherboard I think.  I do know that the video memory was kind of limited; something like 2Mb, with an expansion slot for another 2Mb? (which I haven't found a chip for yet...).

Thanks for the help!....

---

### Post by Theo-Ubu on 2006-05-01
Starting to think this forum is kind of useless.   Too many posters, too few answers.... one's message scrolls off and into oblivion to fast...

---

### Post by r4ik on 2006-05-02
There are many posters you have got valid piont there.
Best thing to do is simply "bump" a thread to get it back under peoples attention.
As for your your install i think your machine is too old to handle Breezy.
Why not try DSL it can be found here it is "live" also with an install option.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

For further questions there is a Mac users Forum section perhaps they can piont you some directions.

[http://www.ubuntuforums.org/forumdisplay.php?f=95](http://www.ubuntuforums.org/forumdisplay.php?f=95)

Good luck !

---

### Post by Theo-Ubu on 2006-05-02
Hey, 

Thanks for the pointers.  I'll give those a try.

---

### Post by Theo-Ubu on 2006-05-02
So I did end up finding the answer to this question in the Apple section of these forums.  It turns out that the default synce and refresh rates for 1024 resolution are incorrect, so the method is to boot up to that black-screen state, then get to a command prompt and use nano text-edit to change the X11 conf file, then switch back to X and kill it, restart it.   Then you can see it booting up desktop.

What I found however is that the distro just crawwwwls along reading from the CD at the 100Mb memory space it has.   I may have to buy a new bigger HD for it, install it onto the actual HD and see how that helps.

From the glimmers that I can see of the desktop, it looks pretty cool though!

Thanks all,
Theo

---

### Post by r4ik on 2006-05-02
Glad you got it working Linear gave a good peace of advice there.
I dont know nothing about Mac
A bigger HD and more memory to get some better performance would not hurt.
Thanks for the reply !

---

