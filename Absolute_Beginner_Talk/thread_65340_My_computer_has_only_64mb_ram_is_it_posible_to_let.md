---
title: "My computer has only 64mb ram is it posible to let it use hard disck memory?"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by Spyware on 2005-09-13
My computer has only 64mb ram is it posible to let it use hard disck memory?

if yes, can you guide how can i do it?

---

### Post by bsussman on 2005-09-13
What you are asking for is called swap space - the on-disk virtual extension to main memory. Ubuntu configures it appropriately when you install.

This swap space is on disk.

There is probably a way to see this in a graphic format.  Sorry - I cannot find it at the moment.

in a console window, you can type:
 ```

less /proc/swaps
``` 

or

  ```

 cat /proc/swaps
``` 

to see the system's usage of swap

---

### Post by wmcbrine on 2005-09-13
Possible? I'd say it's inevitable.

Swap is set up automatically on all Ubuntu systems. You don't have to do anything special; in fact, you'd have to go out of your way to disable it. But with only 64 MB, you'll probably be swapping more than you like. You might want to look into using a stripped-down X environment.

---

### Post by poofyhairguy on 2005-09-13
It will set that up by default. The whole thing will be pretty slow though. 

Look at this link:

[http://ubuntuforums.org/showthread.php?t=42873&highlight=mini+ram](http://ubuntuforums.org/showthread.php?t=42873&highlight=mini+ram)

---

