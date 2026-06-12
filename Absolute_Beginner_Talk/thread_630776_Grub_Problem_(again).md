---
title: "Grub Problem (again)"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Ex-windows on 2007-12-03
Hi all, Here,s another noob in dire need lol.
I have dual boot XP and Fiesty on an 80gig HD. When I tried to log into ubuntu after leaving th eXP side, all I get is a grub> prompt and this message  :[MinimalBASH Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list the possible completions of a Device/filename ]".... Then the is the grub> prompt directly below. If I type help it brings up a list of  alist of what appears to be commands..  Normally there would be the os choices but these are not there, only the grub prompt. This happened once b-4 but I just re installed ubuntu. I would like to learn How do I get my Grub working  again. Thanks in advance.....

---

### Post by Duck2006 on 2007-12-03
This should  help reinstalling grub.

[http://users.bigpond.net.au/hermanzone/p15](http://users.bigpond.net.au/hermanzone/p15)

---

### Post by Don1500 on 2007-12-03
> **Duck2006 said:**
> This should  help reinstalling grub.

[http://users.bigpond.net.au/hermanzone/p15](http://users.bigpond.net.au/hermanzone/p15)

I could have used this yesterday! But I think the link is broken.....

Just checked, yup it's broke try:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Ex-windows on 2007-12-03
WOW, THat was QUICK,
 Thank you for th elink but when I clicked it  The site says the contents cant be listed. Is there another source for the info???
Again Thanks...

---

### Post by ryanVickers on 2007-12-03
the Super Grub Tool in my signature should help pretty much any problem.  Once you've "repaired" it or whatever it does, then if it still doesn't work, boot a live CD and change your /boot/grub/menu.lst partition/hard drive location settings to be what the computer thinks is correct (they're usually quite strait forward, but not always... :p)

---

### Post by Ex-windows on 2007-12-03
Wow, This is why everyone should use ubuntu... Thank you very much I am off to check out both links. Will post results as soon as I can. Thanks very much...

---

### Post by Ex-windows on 2007-12-06
Sorry for the late response. This is a lot more detailed than I thought lol Anyway. Thank you for the links as I was/am able to boot both xp and ubuntu. The trick now is to understand how to fix the grub menu or whatever is making my comp display the grub prompt at startup. In case I dont get back here I hope everyone has a joyous Holiday Season....

---

### Post by Duck2006 on 2007-12-07
If you can't see the grub menu at startup you have to edit the menu.lst and place a # in frount of the hiddenmenu so it looks like

> #hiddenmenu

---

### Post by Ex-windows on 2007-12-07
Thank for the response. I checked out the menu.lst file in the grub folder and it appears to be as you suggest. here is the 3 lines from the file

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Is there anyway to just re install just the grub. Or update it. 
 T. Y. IV 
ANyone???

---

