---
title: "Apple aluminum keyboard"
date: 2009-08-22
forum: Apple Hardware Users
---

### Post by dullo on 2009-08-22
Hi, I am using an apple aluminum keyboard on my computer with Jaunty installed. The keyboard is great however I am using the one without the number pad which also means this keyboard is lacking a Delete Key. 
Is there any way to somehow assign the delete key to one of the Fuction keys at the top? Like F5 or F6?
Can someone tell me how to do this, any helpful response is appreciated.

---

### Post by alexmurray on 2009-08-22
if it has a function key, try pressing that with backspace and it should act as delete

---

### Post by dullo on 2009-08-22
No the function key actually does nothing at whatsoever.
The function key is not fuctional.... ohhhhhh irony..

---

### Post by amd-64 on 2009-08-23
I have a module hid_apple which activates the fn key. Check if it is there using 

$ lsmod | grep apple

This thread has a very detailed guide for mapping keyboard keys including delete 
[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)

---

### Post by dullo on 2009-08-23
> **amd-64 said:**
> I have a module hid_apple which activates the fn key. Check if it is there using 

$ lsmod | grep apple

This thread has a very detailed guide for mapping keyboard keys including delete 
[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)

Yes! that was perfect, thank you so much
I remapped my F5 key to delete

---

