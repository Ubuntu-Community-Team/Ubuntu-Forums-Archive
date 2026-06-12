---
title: "Video Card Issues."
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-17
If this is the wrong kind of thing to ask here simply let me know and I will delete it.

I posted the following question elsewhere, it pertains to WindowsXP but it is related to Ubuntu in a round about way.

(Note I am not asking for any help with the question in the "code" tags. it is only there to help explain my situation.)

```
(Note I left all pictures as links so as not to slow down users with slower connections)
(I have also ran multiple antivirus and antispyware applications both in safe mode and out of it.)
(I am on a laptop)

Since I couldn't find a good solution for my display issue.
http://i75.photobucket.com/albums/i295/Scintillement/7d2dc5b6.jpg
I decided to disable my video card in the hardware manager.
http://i75.photobucket.com/albums/i295/Scintillement/d2cef55f.jpg

After doing so the problem didn't show up, thus leading me to believe the problem is with the video card.

Now after doing the above I found that webpages moved very slowly while scrolling downward.
The only fix I could find for it was to go to Desktop>Properties>Settings>Advanced>Troubleshoot.
From there I had to move the slider all the way to the left and disable Write Combining.
http://i75.photobucket.com/albums/i295/Scintillement/cd5448d1.jpg

Now my question is what is powering my video if I disabled my video card?
Under Desktop>Properties>Settings>Advanced>Adapter I see the following:

http://i75.photobucket.com/albums/i295/Scintillement/bb814d66.jpg

General Tab:
http://i75.photobucket.com/albums/i295/Scintillement/534f98fc.jpg

Driver Tab:
http://i75.photobucket.com/albums/i295/Scintillement/932d6977.jpg

Resources Tab:
http://i75.photobucket.com/albums/i295/Scintillement/48c3ec9b.jpg

Under the Resources tab the Conflicting devices list is:

Input/Output Range 03B0 - 03BB used by:
SiS Accelerated Graphics Port
Input/Output Range 03C0 - 03DF used by:
SiS Accelerated Graphics Port
Memory Range 000A0000 - 000BFFFF used by:
SiS Accelerated Graphics Port

I have no idea what any of that means.

I guess my question in short is;
If my video card isn't providing the display, what is? 
How can I find out how powerful the current display device is?

Thank you.  
```

I have run the LiveCD for Ubuntu 6.06 and found no problems visually. My concern though is that I will install Ubuntu and the problem will appear again. I would not know how to "fix" it if it were to do that.

Does Ubuntu have a way to "fix" (well in this case put a band-aid on) a problem such as that? Sorry to be such a bother.

---

### Post by NESFreak on 2006-07-17
default drivers that work with almoast everything but wont give you many options like hardware accel. teh default linux drivers dont have hardware accel and stuff in moast casses the use software rendering wich is far less hardware dependent.

---

### Post by Scintillement on 2006-07-17
> **NESFreak said:**
> default drivers that work with almoast everything but wont give you many options like hardware accel.

I don't really know what hardware acceleration is but I don't think I *need* it heh. This is an old (2 years or so) Alienware laptop that I want to use to get used to Linux before I buy a desktop. But it's also my only PC at the moment and don't want to fubar anything and be left out in the cold.

Thank you for the response.

---

### Post by NESFreak on 2006-07-17
> **Scintillement said:**
> I don't really know what hardware acceleration is


hardware rendering is when your video card calculates the images that appear.
software rendering is when your normal processor wich calculates also everything else creates the images appearing on your screen.

but it could also be that your windows dirvers are just screwed. try updating them.

if the live cd works then the instalation also works.

---

