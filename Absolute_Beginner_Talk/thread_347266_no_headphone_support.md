---
title: "no headphone support"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by caltabellotta on 2007-01-27
Ever since I installed Ubuntu ( quite recently ), I have never tried using my headphones until last night, when I found that the music still comes out of the speakers even if I plug the phones in.  I do not know what the problem is.  I have an HP pavilion notebook, with two headphone ports.\


Calta

---

### Post by nyinge on 2007-01-27
What do you mean 2 headphone ports?  Isn't the other one for the mic?  Try playing around with the sound mixer.

---

### Post by NeoLithium on 2007-01-27
Open up a terminal window and type:
alsamixer

Make sure your headphones and other appropriate things are turned up; I know my laptop for some reason had a few default muted, which I needed to actually track down and crank up.

---

### Post by caltabellotta on 2007-01-28
I have two options to choose from and make the volume change when utilizing```
alsamixer
```...

master and PCM.  My volume was normal while plugging in the headphones....:confused:

---

### Post by samden on 2007-01-29
I am having exactly the same problem with an Apple iMac G3. This too has two headphone jacks in the front, plus an auxillary sound out plug on the side. Maybe the problem on our computers has something to do with the multiple jacks???

Edit:
I have had a play with alsamixer on my iMac. I found that headphone detection was turned off. However when I turn headphone detection on, then close alsamixer and open it again, headphone detection is again turned off. I cannot seem to turn headphone detection on and make it stay on. This could be your problem as well. Any thoughts anyone?

Thanks

---

### Post by deadgobby on 2007-01-29
Here is a bug link for the HP
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/37055](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/37055)

---

### Post by MC_Jonn on 2007-01-29
This is the same message i posted in another thread.

             Okay this might sound weird, but i kinda "fixed" the problem. The device i use is the Alsa mixer. So while trying out combinations, i stumbled upon this option

                     Double click your volume control. Go to Edit->Preferences. Here tick the External Amplifier box. You get a tab. Now switch to that tab and remove the tick in the External Amplifier box. This will cut out your Speaker sound, but your head phones will still work, then again you will notice a slight drop in audio level boost. Not that it matters, but the real problem is once you remove your headphones, your laptop speakers will NOT automatically continue playing. You again have to go back to the volume control and switch on External Amplifier.

                  I don't know if this is going to work for you, but it did work for me AND its at least a temporary solution, till we can find a permanent one, i.e provided we can............hope it helps!

---

### Post by caltabellotta on 2007-01-31
Nope, still dont have it....

When opening up gnome-voume-control I get the asla mixer with 3 options: PCM, Master, and Capture.  In preferences I only have the ability to deselect these three.

---

