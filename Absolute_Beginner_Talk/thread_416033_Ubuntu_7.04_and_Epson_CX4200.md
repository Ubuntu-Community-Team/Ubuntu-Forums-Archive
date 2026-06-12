---
title: "Ubuntu 7.04 and Epson CX4200"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by piti118 on 2007-04-20
Hi,

I did a fresh install of Ubuntu 7.04. Then I tried to add my printer Epson CX4200. It'd detected and it was added successfully. Note that  the same printer+coupter works together before in 6.10.

However, when I tried to print the test page. The printing light is blinking but it never print anything. It never pull the paper.

So, I went to open office word and tried to type something and print. It pull down the paper but it never prints and the light keeps blinking.

I've tried one of those

chmod a+rw /dev/usblp0

and adding cupsys to plugdev but it doesn't work (the /dev/usblp0 belongs to user root and group lp)

but it doesn't work

Any idea?

Thanks

---

### Post by luke411 on 2007-04-20
I have the 1440 and it does the same, even with Edgy. I found that I had to push the button on the front to get it to print, once the light flashed. It's almost as if it's waiting for permission to print. I just upgraded but haven't tried it yet. I'm still glowing over getting my wireless to work again. Good luck.

---

