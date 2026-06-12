---
title: "onboard problem with visual system beep"
date: 2006-10-18
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-18
Hello, 

Here is how I stumbled on the problem; maybe you can reproduce it: 

- as I am using ubuntu through nx, I activated the visual system beep in the sound control panel
-- the problem does only occur when it is set to flash the entire screen; it does not occur when it is set to only flash the title bar

- firefox is set to begin searching in the current page when I type something 

I navigate to any page and I begin typing a word with onboard; everything goes well until the screen begins to flash to indicate that the word is not present in the page. Then after the flash, the last letter is repeated in the search field of firefox. 

If I continue with typing another letter, the letter appears in the search field, the screen flashes as firefox indicates the error, and afterwards the letter is repeated in the search field. And so on... 


The problem occurs through nx and through vnc. (I cannot try it localy) 


As the problem does not occur when the system is set to only flash the title bar, it does not seem to be very important. 


frafu

---

### Post by t0rtois3 on 2006-10-19
I think I know where the problem is, i'll look at fixing it this weekend.

---

