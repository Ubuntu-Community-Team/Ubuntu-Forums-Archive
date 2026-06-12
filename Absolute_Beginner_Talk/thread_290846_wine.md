---
title: "wine"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-11-01
how the hell do i use wine? i htink i got it installed but when i right click something and tell it to run with wine it never opens

---

### Post by raqball on 2006-11-01
How did you insatll wine?

What ms apps are you trying to run?

How were the ms apps installed?

---

### Post by jpeddicord on 2006-11-01
Usually if you run wine and nothing happens, an error has occured. You must use the terminal to solve the problem. I am assuming that you don't know much about it, but if you do, I apologize.

Open the Terminal from Application > Accessories > Terminal.
Use the command 'cd' to change to the folder where the program you want to run is located. For example, if the program is in /home/username/exes, use this command:```
cd /home/username/exes
```Hit Enter to change to that folder, and then type```
wine program.exe
```where program.exe is the application that you want to run. Wine should then attempt to run it, and then it will show you some errors if it fails.

This is a common method for debugging stuff in Ubuntu, or to see if something went wrong.

Hope this helps,
Jacob

---

### Post by voodoonirvana on 2006-11-01
For the GUI, type winecfg in the terminal. To install an .exe, move the exe to the desired folder and type "wine program.exe". Obviously, you should use the name of the program or installer instead of "program."

---

### Post by bodhi.zazen on 2006-11-01
I did an overview of wine that I hope may help:

[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by jpeddicord on 2006-11-01
> **bodhi.zazen said:**
> I did an overview of wine that I hope may help:

[How to wine](http://doc.gwos.org/index.php/HowToWine)
That's a very nice tutorial :)
I'm going to show this to someone I know that wants to use wine.

---

