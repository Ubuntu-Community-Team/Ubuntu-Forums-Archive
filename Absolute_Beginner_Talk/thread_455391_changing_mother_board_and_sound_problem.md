---
title: "changing mother board and sound problem"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by fire_storm on 2007-05-26
Hi

i changed my mother board to a GA-P965-DS3 and run the same linux as i used to on the old one, every thing is fine but the sound, there is no sound can anyone help please

---

### Post by coffeecat on 2007-05-26
I guess alsa is still configured for the sound card you had in the old motherboard - perhaps a different chipset/make? In any other distro, I'd suggest you ran alsaconf, but alsaconf gives a 'command not found' error in Ubuntu. :roll: However, I believe asoundconf is the equivalent/alternative in Ubuntu.

[This thread]("http://ubuntuforums.org/showthread.php?t=418360&") is not entirely relevant to your situation - it's about a problem upgrading to Feisty - but it gives clear directions on how to use asoundconf. 

I Hope it works for you.

---

### Post by fire_storm on 2007-05-27
no it didnt work but, i found the problem, i have a 5.1 system the side, front were on the lowest.. i had to "show" them and raise the volume.... :popcorn:

---

