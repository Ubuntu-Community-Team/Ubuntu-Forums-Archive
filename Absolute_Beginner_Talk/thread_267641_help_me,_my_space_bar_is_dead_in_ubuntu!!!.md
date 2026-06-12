---
title: "help me, my space bar is dead in ubuntu!!!"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2006-09-28
Hi,

Can anyone pleasepleaseplease help me?

I may have accidentally assigned a keyboard shortcut to the space bar, and now it doesn't work!!!!! I disabled all the keyboard shortcuts, but it still does't work! (it's such a pain to copy-paste spaces!!!!)

---

### Post by sbergman27 on 2006-09-28
> **limitedmage said:**
> I may have accidentally assigned a keyboard shortcut to the space bar,

If you ctrl-alt-f1 to a console does it work there?

(ctrl-alt-f7 will get you back to your desktop.)

---

### Post by ricardisimo on 2006-09-28
> **limitedmage said:**
> Hi,

Can anyone pleasepleaseplease help me?

I may have accidentally assigned a keyboard shortcut to the space bar, and now it doesn't work!!!!! I disabled all the keyboard shortcuts, but it still does't work! (it's such a pain to copy-paste spaces!!!!)

If you type ```
xev
``` in the terminal (you should get a little white box floating off to the side) it will return the value for each key, if it's working at all. It's a starting point, at least.

---

### Post by ricardisimo on 2006-09-28
Also, you should be able to find what <SPACE> is doing in System > Keyboard Shortcuts.

---

### Post by limitedmage on 2006-09-29
thanks a lot! I opened the terminal and now it works! just like that...

I love the fact that after only a couple of hours so many people have answered. Thank you, Ubuntu community!

---

### Post by ricardisimo on 2006-09-29
Hmmm... I not sure that just opening the terminal should have fixed your problem, but I guess we shouldn't look a gift horse in the mouth. Enjoy!

---

### Post by TheMono on 2006-09-29
"Hmmm... I not sure that just opening the terminal should have fixed your problem, but I guess we shouldn't look a gift horse in the mouth. Enjoy!"

Shhhhh.... Don't tell him that! Take the credit for fixing the issue lol.

j/k

---

### Post by hotani on 2006-10-28
I just had the same problem and fixed it by dropping to terminal. Strange, but I had attempted to set the 'pause' key to something in keyboard shortcuts then somehow it became the 'space' key. Spacebar was set to 0x41 (?). So if I wanted to type something I'd have to hit 'pause' instead of the spacebar.

---

### Post by fireflygirl on 2006-11-21
](*,) i am having the same problems with my spacebar and have tried all of your suggestions in this post. is there anythind else i could do. i have just installed ubuntu 6.10. and upon attepmting to fix this i tried logging in as root, but it tells me that root is not allowed to login using the normal login screen. please help, i am but a poor newbie stuck in windows xp pro!!!
 ](*,)

---

