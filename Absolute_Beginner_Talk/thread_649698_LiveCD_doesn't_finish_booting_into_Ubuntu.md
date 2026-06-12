---
title: "LiveCD doesn't finish booting into Ubuntu"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Jamibu on 2007-12-25
Right. Not a complete newbie, but limited enough in knowledge that I've had to come online for help. Had a browse around the forum and not seen anything that matches my problem.

Got the LiveCD finally downloaded correctly, checked the md5sum, perfect match, and the CD has no errors according to the built in CD checker.

I select to run start/install Ubuntu, which starts off with good intentions.

After a little while, it decides that it can't detect my graphics card (laptop computer, S3 Unichrome graphics card) and that I can either configure the video manually or it will just use safe graphics mode. I go through the configuration, and find the correct graphics card and resolution etc.

Clicking OK, it goes through a number more lines of text, before coming to this line:

*Running local boot scripts (/etc/rc.local)                                            [ OK ]

After this, nothing happens. The cursor sits there blinking happily at me, and I tried leaving it for quite a while and still nothing happened.

As a precaution I decided to try running it in safe graphics mode after all, to the same result.

I would love to give Ubuntu a try, but so far I can't even get to the desktop :(

Any and all help would be appreciated :-)

---

### Post by tibellus on 2007-12-25
Something similar happened to me. You "believe" that the driver you chose is the one for your video card. In fact, it might not work well with it. You should try to reconfigure the xorg server and use a different driver, try a generic one for the moment. I used tglx (I don't know if that's the exact name :D ) and worked... I hope this helps, please post an answer just to let me know if this helps:)

---

### Post by Jamibu on 2007-12-25
Well surely this would be solved if I went into safe graphics mode? Yet I end up with the same result. Will try your driver later just in case though. 

EDIT: btw, do you mean to use that driver where it asks me to select a video driver? Or to change some other setting?

---

### Post by tibellus on 2007-12-25
> EDIT: btw, do you mean to use that driver where it asks me to select a video driver? Or to change some other setting?

I mean you should use it when you're asked about the video driver. I didn't change anything else when this happened to me.

---

### Post by Jamibu on 2007-12-25
No such luck I'm afraid.

Still just sits doing nothing after that same line that I posted earlier

---

### Post by spiderbatdad on 2007-12-25
have you tried entering boot parameters from the grub boot screen F6? I think F1 then f6 gives a list of special parameters. I had great luck on an older HP recently by deleting rw quiet splash ( i think it was) and replacing with noapic nolapic vga=771. I did not use -- . It took quite a few tries to get the parameters just right. I must have tried to load it 20 times or more. It did finally like the parameters and load.

---

