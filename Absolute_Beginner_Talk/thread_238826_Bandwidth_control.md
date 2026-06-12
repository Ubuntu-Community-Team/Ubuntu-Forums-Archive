---
title: "Bandwidth control"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by VictorGavrish on 2006-08-18
Can I limit the internet bandwidth available for an application in Ubuntu? Or list applications which would have a higher priority to use the internet connection? I want to be able, for example, to browse the internet with Firefox while dowloading software with apt-get. Currently, Firefox would very reluctantly load web pages if it would load them at all.

Editted to add:
apt-get got broken when I was doing the procedure below. Can somebody help me to fix things to work at least how they had before?

---

### Post by bluefrog on 2006-08-18
for apt-get have a look at [http://www.ubuntuforums.org/archive/index.php/t-20342.html](http://www.ubuntuforums.org/archive/index.php/t-20342.html)

THis might help you I hope.

James

---

### Post by VictorGavrish on 2006-08-19
Nope, doesn't seem to work for me :( On line three, bash reports:
bash: usr/lib/apt/methods/http: No such file or directory

Now, I wonder if executing the first two commands changed something in my system which would slow down or even break something in apt-get? I honestly don't understand what they do :)

Isn't there I GUI for a thing like this though? It isn't very handy to type in obscure commands every time you want to change the bandwidth :-/

---

### Post by VictorGavrish on 2006-08-19
It did break apt-get! How do I reverse the first two lines?

---

