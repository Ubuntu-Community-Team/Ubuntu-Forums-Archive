---
title: "Firefox"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by DianneT on 2006-01-14
Im using Kubuntu breezy badger, and i went out and bought myself "linux bible 2005 edition" and thats helped through a bit, but i just cant seem to be able to install firefox, i basically dont have a clue what im doing

---

### Post by aysiu on 2006-01-14
Press Alt-F2
Type ```
konsole
```
Then a DOS-like Window will pop up. Once there, type ```
sudo apt-get update
sudo apt-get install firefox
``` 

For more on how to install software, read the second link of my signature.

---

### Post by DianneT on 2006-01-14
I did that thanks.
and i typed in firefox (should i have done that?) into konsole and it came up with  
Alert
The file /usr/share/ubuntu-artwork/home/index.html cannot be found. Please check the location and try again.

any suggestions?? please
Im using konqueror as a web browser adn i dont like it

---

### Post by Nameless on 2006-01-14
[QUOTE=DianneT]I did that thanks.
and i typed in firefox (should i have done that?) into konsole and it came up with  
Alert
The file /usr/share/ubuntu-artwork/home/index.html cannot be found. Please check the location and try again.

[/QUOTE]

In the bottom left corner, there should be a "K" button.  If you hit that it will bring up a list of folders/programs and find Internet > Webrowser (Firefox) and you'll be all set. 

Once you have the program you don't necessarily need to run it from terminal.

---

### Post by aysiu on 2006-01-14
[QUOTE=DianneT]
and i typed in firefox (should i have done that?) into konsole and it came up with  
Alert
The file /usr/share/ubuntu-artwork/home/index.html cannot be found. Please check the location and try again.[/QUOTE] That's a bug. The default homepage for Firefox is /usr/share/ubuntu-artwork/home/index.html, but I think if you have Kubuntu instead of Ubuntu that file doesn't exist.

Just change your homepage to [http://www.google.com](http://www.google.com) or something else, and that error should go away.

---

