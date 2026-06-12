---
title: "Help to install a program please"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-09-06
Hi
I'm trying to install an OCR program in Ubuntu 6.06 Dapper.
The program is called OCRAD and the website is:-http://www.gnu.org/software/ocrad/ocrad.html
I've downloaded a deb file:- ocrad_0.15-1_i386deb
But when I run it I get a message:- Error: Dependency is not satisfiable: libgcc1
I've looked in my Synaptic Package Manager and it shows libgcc1 is installed.
Is there something I can do, or is this deb file not suitable for Dapper?

---

### Post by skymt on 2006-09-06
It might need a different version of libgcc1 than Ubuntu uses. Why not use the ocrad from the repositories?

---

### Post by ron999 on 2006-09-06
Hi skympt
I forgot to look there!
I'll do it now, thanks

---

### Post by ron999 on 2006-09-06
Hmmm
I've installed it from the repository - next question - how do I get it to run?

---

### Post by petri on 2006-09-06
In your terminal write: ```
ocrad
```

You don't find it in Program menu? Try in terminal with ```
killall gnome-panel
```

Still no luck? Find Alacarte in your Program menu (accesories?) and make an entry for ocrad. And to find the program you can use ```
whereis ocrad
```

---

### Post by ron999 on 2006-09-06
Hi petri/skymt
Typing ocrad at the terminal does nothing.
I've found ocrad using whereis and I've made a menu entry, but when I select it nothing happens.
I'd better read up on the program from the webpage - unless you can suggest anything else?

---

### Post by ron999 on 2006-09-06
I'm getting somewhere now.
ocrad's a program to be used from the terminal.
Got to type ocrad [filename]
eg ocrad /home/ron/out.pnm
Then it prints it out - in the terminal.
After that I can copy and paste into a text editor or word processor.

---

### Post by monktbd on 2006-09-06
try
> ocrad /home/ron/out.pnm > output.txt

then you have it already in a file you can open.

---

### Post by Tomosaur on 2006-09-06
You can just redirect the output directly to a file if you like:
```

ocrad /home/ron/out.pnm > ocradOutput.txt

```

---

### Post by ron999 on 2006-09-06
Hi monktbd/Tomaosaur

ocrad /home/ron/out.pnm > output.txt 
ocrad /home/ron/out.pnm > ocradOutput.txt

Yes, this works perfectly, thanks.:)

---

