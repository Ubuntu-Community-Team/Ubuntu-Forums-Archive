---
title: "my laptop doesn't switch headphones and speaker correctly"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-01-29
Hi, i just installed edgy and it works great except for the fact that when i resume the computer from a suspend/hibernate, the sound is really stuffed up. Sometimes only the speakers will play sound, and the headphones do not play sound, sometimes only headphones get the sound, and other times, both headphones and speakers are on. Is there a way to fix this?

---

### Post by morfeibg on 2007-01-29
Hello,

I have Dell inspiron E1505 and have similar problem. Ubuntu Edgy doesn't recognize when I plug in my headphones and as result I hear sound from both the speakers and the headphones.

---

### Post by MC_Jonn on 2007-01-29
Hi
           I got the same problem on my lenovo too, in fact i started a thread before this one asking a solution for this problem. The sound comes from both the headphones and the laptop speakers. It must be the drivers,I specially never tried to configure them,
          Maybe we've got something in common, do you people also have on board Intel Sound card or something else?

---

### Post by davidY on 2007-01-29
Wow, we all seem to have these types of errors... considering that it seems like two types of dell laptops and a lenovo one have the same problem, but there are heaps of laptop ubuntu users who don't have this problem, this must be some problem with our configuration or something. Btw, I have a dell d620 latitude

I tried to use the alsactrl to control the alsa settings by saving and restoring, but that seemed to have no effect whatsoever.

---

### Post by MC_Jonn on 2007-01-29
Okay this might sound weird, but i kinda "fixed" the problem. The device i use is the Alsa mixer. So while trying out combinations, i stumbled upon this option
     

                                             Double click your volume control. Go to Edit->Preferences. Here tick the External Amplifier box. You get a tab. Now switch to that tab and remove the tick in the External Amplifier box. This will cut out your Speaker sound, but your head phones will still work, then again you will notice a slight drop in audio level boost. Not that it matters, but the real problem is once you remove your headphones, your laptop speakers will NOT automatically continue playing. You again have to go back to the volume control and switch on External Amplifier.


          I don't know if this is going to work for you, but it did work for me AND its at least a temporary solution, till we can find a permanent one, i.e provided we can............hope it helps!

---

