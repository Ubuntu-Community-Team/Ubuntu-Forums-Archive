---
title: "Linux Terminal open command in new window"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by AustinMarton on 2007-10-06
When I start an application from the terminal (e.g. 'gedit file.txt') I have to wait for the application to finish before I can execute another command.

Is there some sort of suffix (or something) that I can add to the command to make it open in a new window so I can keep using the shell I have open?

Cheers,
Oz.

---

### Post by Pumalite on 2007-10-06
You can have as many Terminals open as you want.

---

### Post by w7kmc on 2007-10-06
> **AustinMarton said:**
> When I start an application from the terminal (e.g. 'gedit file.txt') I have to wait for the application to finish before I can execute another command.

Is there some sort of suffix (or something) that I can add to the command to make it open in a new window so I can keep using the shell I have open?

Cheers,
Oz.

gedit file.txt &

(append the &....that is what you are looking for...

---

### Post by AustinMarton on 2007-10-06
Absolutely brilliant, the '&' is exactly what I was looking for. Thanks w7kmc!

---

### Post by w7kmc on 2007-10-08
No problem...

Also, if you happen to forget the &  say you type 

gedit file.txt

and hit enter....and you want the prompt back....you can place the gedit job in the background by these to commands in the  terminal:

<cntrl>-z
bg

---

