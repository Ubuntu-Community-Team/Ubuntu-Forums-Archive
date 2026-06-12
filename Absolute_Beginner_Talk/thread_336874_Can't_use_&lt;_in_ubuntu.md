---
title: "Can't use &lt; in ubuntu"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Nirc on 2007-01-12
I think the title pretty much says it all really for some reason I can't use the < symbol in ubunu the button works as I can use , and < works in windows. I couldn't find any other posts with people with this problem, could the cause be that I have a non-standard keyboard with 14 extra buttons? I couldn't find a similar keyboard in the list to choose from so I went for generic 105 keyboard. Can anyone help? Its getting quite annoying having to google for the symbol everytime I want to use it....

---

### Post by Tomosaur on 2007-01-12
I guess it could well be your non-generic keyboard yeah. Have you tried testing the other keys on your keyboard to see if it's just a mapping problem? Certain geographic settings put keys in different places. For example, your tilde key (~) may be next to your 1 key, or it may have it's own key. Best bet is to try other keys (using shift aswell) to see if the < is mapped to somewhere else.

---

### Post by Nirc on 2007-01-12
I just tried the other keys and they're all okay its just the < symbol that doesn't appear.

---

### Post by Tomosaur on 2007-01-12
A work around for the time being is to go to Start > Accessories, then click on the Character Map app. It's not ideal, but it should work for now.

I'm sure I've encountered a very similar problem before, I'll try to find out what I did to fix it.

---

### Post by Tomosaur on 2007-01-12
Ok, think I may have got it. Please paste the output of this command in a terminal:
```

xmodmap -pk | grep 'guillemot'

```

---

### Post by Nirc on 2007-01-12
The ouput is :
     52         0x007a (z)      0x005a (Z)      0x00ab (guillemotleft)  0x003c (less)   0x00ab (guillemotleft)  0x003c (less)
     53         0x0078 (x)      0x0058 (X)      0x00bb (guillemotright) 0x003e (greater)        0x00bb (guillemotright) 0x003e (greater)

---

### Post by Tomosaur on 2007-01-12
Ok, now does your > key work ok? If so, assuming the > key is '53', count to the < key, assuming left is less and right is more. I.E: on my keyboard, my count goes:
52 53 - because my < is immediately to the left of the > key. If you had another key, let's say the / key in between the two, you would end up on 51:

<  /  >
51 52 53

---

### Post by Nirc on 2007-01-12
The > key works fine and < is immediatly to the left of the > key so the numbers are correct (> is 53 and < is 52). Also , works okay so the actual button works it's just when I push shift nothing happens.

---

