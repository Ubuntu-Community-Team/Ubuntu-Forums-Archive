---
title: "no sound"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by Loony on 2005-10-19
:confused: 
Can anyone tell me how to get sound on my ubuntu in easy terms?
If I go to preferences then multimedia it will play some soumds but as soon as I close the window the sounds stop!
Can anyone help me?  I am almost illiterate in computer terms!

---

### Post by rubycon on 2005-10-19
When in Preferences -> Multimedia Systems Selector, select the ESD mixer for output. After that you have to make sure that is the mixer you use in your music or videoplayer of choise.

---

### Post by patrick295767 on 2005-10-19
alsamixer & 
can help sometimes 
  
   
chmod 666 /dev/dsp 
for permissions
  
that helped me a lot !

pat'

---

