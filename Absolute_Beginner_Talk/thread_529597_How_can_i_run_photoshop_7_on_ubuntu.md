---
title: "How can i run photoshop 7 on ubuntu?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Saulie on 2007-08-19
Heya, im really new to ubuntu and I just got it a few days ago. I have allways used photoshop to design things and all of the designs that I have are .psd. I understood that gimp would open it and i assumed that it would all work just as photoshop however now i have discovered that you cannot edit layers as in change the text from the psd or anything.

So now i have been hearing about people running photoshop seven and cs through wine. I dont have the photshop seven or cs cd or serial ect, would ti be possible to get a thirty day trial of photoshop seven or cs running on ubuntu through wine?

If so could someone talk em through it or show me a tutorial of some sort?

Cheers, Saulie.

---

### Post by hyper_ch on 2007-08-19
yeah, trials would work the same as the full version.

---

### Post by Hobo Joe on 2007-08-19
You can use Wine.

[http://www.winehq.org/](http://www.winehq.org/)

[http://appdb.winehq.org/appview.php?iAppId=17](http://appdb.winehq.org/appview.php?iAppId=17)
This tells how well each version works with WINE, as you should be happy to see, 7.0 has a 'Platinum' rating. :)

---

### Post by Saulie on 2007-08-19
Okay, does anyone happen to know where I could get the trial download, I cant find it on the adobe site for some reason.

Cheers, Saulie.

---

### Post by Saulie on 2007-08-19
Okay well i have installed photoshop seven through wine, just where do I open it from? It isnt listed in the applications menu..

---

### Post by hyper_ch on 2007-08-19
```

wine ~/.wine/drive_c/path/to/photoshop/photoshop.exe

```

or something like that.

---

### Post by Saulie on 2007-08-19
Okay thanks for that I have found where it is and tried to run this:

```
wine ~/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe
```

But it doesn't take in the space, what do i replace the space with?

---

### Post by Saulie on 2007-08-19
Okay how do i get the exe file to run? When i go to Wine File and then select Photoshop.exe i get a failed to initialize vbox message.

Help please? =S

---

### Post by mc4man on 2007-08-19
I haven't used PS since I switched from xp (using gimp) so I don't know if it works
I'd try running from the terminal using this as a guide
```
wine '/home/doug/.wine/drive_c/Program Files/ImgBurn/ImgBurn.exe' 
```
note use quotation marks and change imgburn to your photoshop path
If you can't get any specific help I have a copy I'll try installing after dinner
what version of wine are you using?

---

### Post by Saulie on 2007-08-20
Heya, i have found a bug report on the wine site that seems to fix the problem i am having, however I cant understand what to do.

[http://bugs.winehq.org/show_bug.cgi?id=4635](http://bugs.winehq.org/show_bug.cgi?id=4635)

If someone could help me here I would be more than grateful as i cannot edit any of my psd's without photoshop, and i have to finish off some work for some clients in the next few days.

Thanks, Saulie.

---

