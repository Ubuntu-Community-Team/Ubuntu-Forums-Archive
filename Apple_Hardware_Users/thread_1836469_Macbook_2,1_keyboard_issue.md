---
title: "Macbook 2,1 keyboard issue"
date: 2011-08-31
forum: Apple Hardware Users
---

### Post by derrichter on 2011-08-31
After installing Xubuntu 11.04, I noticed a (I supposed so you know :D ) stupid problem: I can't do any symbol which requires the "alt + button" command in Mac OSX, such as the <at>. I tried switching keyboard layouts but I just couldn't solve this problem. Thanks. :)

---

### Post by pauljwells on 2011-09-02
What do you have in your Keyboard Preferences (look in system preferences)?

United Kingdom Macintosh / 105 key PC Intl works for me.

I also have a local ~/.Xmodmap file:

```
keycode 94=grave asciitilde grave asciitilde dead_grave dead_horn
keycode 49=section plusminus section plusminus section plusminus
```

to get the 'fiddly keys' working.

You may need different settings depending on your keyboard but these two things are the places to start looking

---

