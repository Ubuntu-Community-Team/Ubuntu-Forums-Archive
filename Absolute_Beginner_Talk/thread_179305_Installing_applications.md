---
title: "Installing applications"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by sanderella on 2006-05-19
Hi guys!

I'm working my way through [http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)
trying to install RealPlayer 10 as described. 

I'm on section 3, where it says, "Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin"

How do I make the downloaded file executable? I can't see a command line. What am I missing?

Grateful for any help, thanks

---

### Post by Ubuntuud on 2006-05-19
Start up a terminal. Type "cd /directory/where/the/file/is" (without the ""). Then type: "chmod +x RealPlayer10GOLD.bin".

---

### Post by Klaidas on 2006-05-19
You can't find the command line (aka Terminal)? :)
No problem. If you're using GNOME, it's Applications -> Accesories -> Terminal
If you're using KDE, it's Applications -> Accessories -> Terminal

---

### Post by louis_nichols on 2006-05-19
well, that right there is the command you ave to use to make the file executable :)

so, you have to go to **Applications>Accessories>Terminal** (so this the way you get a command line - well, one of them) then in there navigate to where the package is, using the command **cd** (change directory) and once where the file is, issue that command:

```
chmod +x RealPlayer10GOLD.bin
```

---

### Post by Al3xanR0 on 2006-05-19
[QUOTE=Ubuntuud]Start up a terminal. Type "cd /directory/where/the/file/is" (without the ""). Then type: "chmod +x RealPlayer10GOLD.bin".[/QUOTE]

Once you have done this you can allow Synaptic to complete the install or just ```
./RealPlayer10GOLD.bin
``` in the directory where RealPlayer10GOLD.bin is located (from the terminal of course) it is just as easy.

---

### Post by sanderella on 2006-05-19
Thanks guys!!

---

