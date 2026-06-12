---
title: "XCalib Mac problem"
date: 2008-02-14
forum: Apple Intel Users
---

### Post by self-defence on 2008-02-14
Hi,

I've got a MacBook Pro running Ubuntu 7.10. Now the problem was that everybody told me that all of my photos that I retouched in Gimp were to dark. When in fact on my Mac the photos seemed quite vivid. So I installed XCalib and loaded the MacOSX profile just like in the wiki. But now not only do the photos seem even darker on other monitors (or when printer) but even the color saturation and white balance is way off. I've tried compensating by hand in Gimp but I get an even more disastrous outcome. And also it doesn't matter if I work under full brightness of the LCD or the least the image is still off.

Anyone have any idea how I could get the right colors on the Mac LCD monitor?

Thanks for the input in advanced and a nice day to all.

---

### Post by cyberdork33 on 2008-02-14
> **self-defence said:**
> I've got a MacBook Pro running Ubuntu 7.10. Now the problem was that everybody told me that all of my photos that I retouched in Gimp were to dark. When in fact on my Mac the photos seemed quite vivid. So I installed XCalib and loaded the MacOSX profile just like in the wiki. But now not only do the photos seem even darker on other monitors (or when printer) but even the color saturation and white balance is way off. I've tried compensating by hand in Gimp but I get an even more disastrous outcome. And also it doesn't matter if I work under full brightness of the LCD or the least the image is still off. 

After using xcalib, you are probably displaying images correctly... I would say that the problem has to do with the color profile that you are using in Gimp. I am no expert, but from your description, I would guess Gimp to be culprit and really has nothing to do with the fact that you are on a Mac (at least now that you fixed your display's color profile.)

---

### Post by self-defence on 2008-02-14
Ok cool. Thanks I never thought of it that way and you might be on to something. But I don't think I ever changed anything in Gimp nor was I aware that I could use a profile in Gimp. Any idea how to check this in Gimp?
And there's another thing that I thought of just now. If it was just the Gimp profile wouldn't then the image look really great in Gimp and not that good in let's say EyeOfGnome and not that good on any other monitor. In my case the image looks ok in Gimp and also ok everywhere else on my pc. But when I open the same image on any other pc it's to saturated and dark.
Could it really be the Gimp profile or is could there be something else wrong?

Thanks again.

---

### Post by cyberdork33 on 2008-02-14
well, putting it that way, maybe not... Still, I would try.

Open Gimp, go to File > Preferences, and there is a Color Management Selection on the Left side of the preferences dialog. (Sorry if this is not exactly right for you, I am checking this in Windows on Gimp 2.4.3) There is place to define a RGB color profile, CMYK, and monitor (there are also some printer options). Setting these should get everything in sync, and then what you see, should be the actual look.

---

### Post by self-defence on 2008-02-15
Cool cyberdork33, thanks. I setup Gimp so that it tries use monitor profile and tried to even less filter my image an got a better result. The image still looks more vivid on my monitor than on another machine but I'll try to play around with Gimp settings a little more and see if I get an even better result.
Just to cover all my bases here, could it be anything else you could think of?

Anyway thanks again.

Bye

---

### Post by cyberdork33 on 2008-02-15
> **self-defence said:**
> Just to cover all my bases here, could it be anything else you could think of?Apple cinema displays are awesome?

You might ask in one of the more general forums as I still don't think it is Mac specific.

---

### Post by self-defence on 2008-02-16
As fare as I'm concerned the display has a really nice and vivid picture. But the difference is bugging me.

Anyway thanks for now cyberdork33.

Bye

---

