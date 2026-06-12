---
title: "iPods"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Vossler on 2006-11-20
So yeah, basically all I want to know is how do I update my iPod using Amarok?
I tried to figure it out but I couldn't...Considering I'm very new at even linux in general.
I have a close friend helping me through everything, so I get the general idea, but he doesn't have an iPod so he doesn't know what to do.

Oh, and I use Edgy btw.
So yeah, all i want to know is how to update and manage my ipod just like itunes, only using amarok.

Thanks. :)

---

### Post by richardward101 on 2006-11-20
stick the files you want in the playlist in amarok, then click media devices (down the left hand side). select your ipod from the list, then drag files from the playlist into the list of files/folders on your ipod.

Alternatively install gtkpod, its simple and streamlined.

If that doesn't help. post more about what you tried/what didn't work, etc.

---

### Post by Vossler on 2006-11-20
Yeah, i tried it, but my ipod isn't showing up in the list of devices.
It's not recognizing that it's there.

And I tried the gtkpod, i downloaded it, and this is going to sound stupid, but i couldnt figure out how to install it. ](*,)

---

### Post by scxtt on 2006-11-20
it would be easier for you to do:

**sudo aptitude install gtkpod**

just make sure you have the *universe* repo enabled in your /etc/apt/sources.list

---

### Post by CordlezToaster on 2006-11-20
> **scxtt said:**
> it would be easier for you to do:

**sudo aptitude install gtkpod**

just make sure you have the *universe* repo enabled in your /etc/apt/sources.list

does this mean you will install the program from the internet?

---

### Post by scxtt on 2006-11-20
> **CordlezToaster said:**
> does this mean you will install the program from the internet?yes, aptitude will source your /etc/apt/sources.list and grab the install files (+ any dependencies) from the internet ... if gtkpod is on a CD, you can add a CD-ROM to /etc/apt/sources.list and install it from there ...

---

### Post by richardward101 on 2006-11-20
When you plug in your ipod, does an icon for it appear on your desktop? If so, open it up, and find out which folder its mounted in (look at the path at the top of the window).

---

### Post by richardward101 on 2006-11-21
another quick question, how did you install amarok? If you downloaded it to install it then that could be why ist not working with the ipod. If you install it instead using the method described above for gtkpod, you may have better luck.

---

### Post by Vossler on 2006-11-21
ah, i seemed to have figured it out.

thanks for your help though guys. :)
gtkpod, FTW. ;)

---

