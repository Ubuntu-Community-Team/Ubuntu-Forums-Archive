---
title: "Broke Key"
date: 2010-11-20
forum: Apple Hardware Users
---

### Post by Viglen on 2010-11-20
I broke my underscore key on my macbook 1.1 keyboard. Is there a way I remap one of the other keys to have the same function. 

Ubuntu 10.04

Cheers

---

### Post by Viglen on 2010-11-20
Almost got it, 
1. Open Terminal and type "**xmodmap -pke**"
2.Find the keycode number of the key that broke and the function it did . 
       The format is keycode (NUMBER)= function
3.to allocate a new key "**xmodmap -e "keycode (NUMBER) = function"**"
4. Make an .Xmodmap in the home directory with **keycode (NUMBER) = function**

Wish I found this at the start
[http://ubuntuforums.org/showthread.php?t=106209]("http://rollingrelease.com/system/2010/09/xmodmap-hints-and-tips")

Finished

---

### Post by Viglen on 2010-11-21
Also works on X11 applications inside leopard as well, so like Gimp and I think Open Office is X11.

---

