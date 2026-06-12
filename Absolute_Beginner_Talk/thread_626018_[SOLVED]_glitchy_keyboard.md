---
title: "[SOLVED] glitchy keyboard"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-11-28
i have a problem with the keyboard cursor randomly shift left or jump around the sentence or webpage occasionally when i am typing. oddly, it doesnt do this in windows, i am using an acer 5610z laptop and ubuntu 7.10 gutsy gibbon. i also had this problem with feisty fawn. 

any solutions?

---

### Post by Grey Box on 2007-11-28
This is an issue due to your touchpad being over-sensitive while you type. Vibrations and accidentally brushing the touchpad as you type can cause this problem. I get it too with my Dell laptop and (used to) with my macbook. 

The solution is to disable the touchpad during keypresses, with eg: a 1 second delay.

In your xorg.conf there is a way to do this and there are various approaches to the problem in [another thread]("http://ubuntuforums.org/showthread.php?t=623346&highlight=touchpad+disable").

I hope that helps. Cheers!

---

### Post by Quash on 2007-11-28
You can adjust the sensitivity in the mouse settings under System>Preferences> Mouse  you should be able to adjust the sensitivity.  Ive got mine fairly low

---

### Post by thebestofall007 on 2007-11-29
reducing the sensitivity of the touchpad worked. thank you. i also found that disabling the tap the pad to click feature worked.

---

