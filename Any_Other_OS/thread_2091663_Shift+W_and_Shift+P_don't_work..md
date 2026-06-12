---
title: "Shift+W and Shift+P don't work."
date: 2012-12-05
forum: Any Other OS
---

### Post by ElStellino on 2012-12-05
Hello folks, as the title says.

I was in search of an easy way of modifying my keyboard layout and followed the trending result in google, using xmodmap. I tried to modify the Caps Lock (key that I hate) in order to make it work as a left shift:

```
xmodmap -e 'keycode 66=Shift_L'
```Now, it happens that when I press Shift+W or Shift+P nothing happens, and I cannot work out why. I didn't modify Shift, and I didn' even think of w or p keys...

Also, this xmodmap instruction modifies the keyboard at a different level than the simple layout. I modified the Caps Lock key in the Italian layout, but also the Spanish layout is affected.

I tried to look in the keyboard shortcuts but no Shift+W or Shift+P are assigned to any instruction. I tried to roll back to the 3.5 Kernel, but no joy. (now I'm on 3.6.7)

Could somebody help me out please?

---

### Post by ElStellino on 2012-12-06
Ok, I solved in this way because I really needed the thing working.
[http://community.linuxmint.com/tutorial/view/170](http://community.linuxmint.com/tutorial/view/170)
I didn't delete though, but cut and pasted in the Windows partition. Now I am pasting pack folders and files one by one, checking that the Shift+W and Shift+P continue to work.

---

