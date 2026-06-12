---
title: "Keymap changes not working properly"
date: 2015-10-14
forum: Apple Hardware Users
---

### Post by philipp-j-fritz on 2015-10-14
Hello Community,

I wanted to switch the left ctrl with the left cmd key. So i made this Xmodmap file and applied this with "xmodmap Xmodmap". Now the left ctrl acts like the cmd key before, but the cmd key works in another way as the ctrl key before. When I press the left cmd key now, it acts like cmd key before. I analyzed it with "xev", but xev says, that I'm pressing the left ctrl key when I'm pressing the cmd key. It should work, but it isn't. Has anybody a solution for me?

BTW: How do I change the switch between windows shortcut? I didn't find this in the preferences.

Here's my XModmap file:

```
[COLOR=#232A2A][FONT=Helvetica Neue]clear control
clear mod4

keycode 105 = 
keycode 206 =
 keycode 37 = Super_L NoSymbol Super_L
keycode 133 = Control_L NoSymbol Control_L

add control = Control_L
add mod4 = Super_L[/FONT][/COLOR]
```

---

