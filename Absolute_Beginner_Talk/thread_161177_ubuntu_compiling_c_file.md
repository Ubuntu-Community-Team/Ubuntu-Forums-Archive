---
title: "ubuntu compiling c file"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by danieljamestravers on 2006-04-16
hi all, 

i am having a problem with compiling a c file (catme.c). 
in ubuntu when i run the root terminal i try:

cc catme.c -o catme

(i get a response saying that the 'cc' command isnt recognized, so i tried...)

gcc catme.c -o catme

(still get the same response)



i dont know what to do (since im relatively new to the whole unix/linux/ubuntu thing).

can anyone please help?

thanks to you all for your replies in advance.

---

### Post by Kronoz on 2006-04-16
Terminal: sudo apt-get install gcc g++

---

### Post by mostwanted on 2006-04-16
[QUOTE=Kronoz]Terminal: sudo apt-get install gcc g++[/QUOTE]

No, don't do that, that will most likely not work properly. To get all basic compiler tools do this:

```

sudo apt-get install build-essential
```

---

### Post by danieljamestravers on 2006-04-16
do i just type that into the root terminal prompt?

---

### Post by mostwanted on 2006-04-17
No, type that into the standard terminal. You can also open Synaptic (System &#8594; Administration &#8594; Synaptic Package Manager), search for the package and install it.

---

