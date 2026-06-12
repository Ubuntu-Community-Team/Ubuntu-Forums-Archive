---
title: "VirtualBox guest (WinXP) will not recognize sound/video cards"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by CRIMPS on 2007-05-12
I have installed WinXP as a virtual machine using Virtual Box.  Host is Ubuntu Feisty.  I can't seem to get Window to recognize my Audigy 2ZS sound card.  I believe this is probably a conflict error because the same card is being used by Feisty as well, although this is more of a guess than an educated theory.  

Does anyone know how to configure this with their virtual machines?  I even tried to just install drivers, but I haven't even had success with this.  

Being that I am running a Virtual machine, I can't enable the card in the BIOS...I am kind of at a loss as to what to do next...

Thanks for the help.  

Z

---

### Post by kyphi on 2007-05-12
When you first start VirtualBox, go to the right side of the screen to Audio, left click and on the resulting screen check the box to enable audio and select Alsa Audio Driver.

That worked for me.

---

