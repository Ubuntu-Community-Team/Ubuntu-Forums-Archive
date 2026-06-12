---
title: "Problem changing keyboard layout in kde"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by anthemius on 2007-06-09
Hi to everyone.

I have a wired problem.

I had installed beryl when suddenly I realized that the key combination for changing keyboard layout from US to GREEK and vice versa, had been changed. Instead of "alt + Shift"  "ctrl + alt + k" it was in use. What is more, the new key combination was changing my layout from US to GREEK but not the opposite. If I want to change back to US layout I have to do with hand.

So I decided to uninstall beryl to see what happening next. Sadly the same behavior .

I don't have problem with what combination to use and I know how to change it.My problem is that my keyboard is switching only to the next layout without doing the same when I press the  combination.

Thanks in advance!!!

---

### Post by ronocdh on 2007-06-09
> **anthemius said:**
> Hi to everyone.

I have a wired problem.

I had installed beryl when suddenly I realized that the key combination for changing keyboard layout from US to GREEK and vice versa, had been changed. Instead of "alt + Shift"  "ctrl + alt + k" it was in use. What is more, the new key combination was changing my layout from US to GREEK but not the opposite. If I want to change back to US layout I have to do with hand.

So I decided to uninstall beryl to see what happening next. Sadly the same behavior .

I don't have problem with what combination to use and I know how to change it.My problem is that my keyboard is switching only to the next layout without doing the same when I press the  combination.

Thanks in advance!!!
Although it's theoretically possible this trouble is somehow hardware-related, I think it's much more an issue related to KDE. I would try posting in the Desktop Environments forum and see whether anyone there can help you. That said, please remember to append a solution to this thread, when you find one!

---

### Post by anthemius on 2007-06-20
I am happy to announce the solution for this problem (it was really an annoying thing for my desktop).

The solution: First of all I had to deactivate the "kxkb" option from the contol center of KDE (Regional & Accessibility --> Keyboard Layout).

That because if it is activated it prevaisl against other setting (by default is not activated).

Then I had to add the following lines at /etc/X11/xorg.conf:

   option "XkbRules"   "xorg"
   Option "XkbModel"   "pc101"
   Option "XkbLayout"  "us,gr"
   Option "XkbOptions" "grp:alt_shift_toggle".

Finally restart or kill kdm and startx again to see the results.

References to everyone able to read greek:

[http://members.hellug.gr/djart/articles/grlinux/grlinux-6.html](http://members.hellug.gr/djart/articles/grlinux/grlinux-6.html)
[http://members.hellug.gr/djart/articles/grlinux/grlinux-3.html#ss3.3](http://members.hellug.gr/djart/articles/grlinux/grlinux-3.html#ss3.3)

---

### Post by diskotek on 2007-09-30
i had the same problem, i found another solution for that in gentoo forum.
just simply open terminal and type

```
setxkbmap -model pc105 -layout tr -variant basic 
```

well change "tr" part in order to your keyboard language (like gr, us etc..). that was working for me....

---

### Post by spankkie on 2008-07-06
> **diskotek said:**
> i had the same problem, i found another solution for that in gentoo forum.
just simply open terminal and type

```
setxkbmap -model pc105 -layout tr -variant basic 
```

well change "tr" part in order to your keyboard language (like gr, us etc..). that was working for me....




OMG! i love you man... this worked like a charm and i dont feel like a lepper anymore trying to remember what key to press when holding right alt key to get a question mark sheeeeeeeeeeeesh!!!!! tyvm

---

