---
title: "Conky"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-02
Could somebody please point me to a step by step tutorial in getting conky to work on ubuntu feisty,

thanks :)
Ajeffreys

---

### Post by SOULRiDER on 2007-06-02
Just install it, make or copy a .conkyrc script and run it :)

---

### Post by bone43 on 2007-06-02
> **ajeffreys said:**
> Could somebody please point me to a step by step tutorial in getting conky to work on ubuntu feisty,

thanks :)
Ajeffreys

I would be interested in this also I have installed conky and could never get it working at least with beryl an a ATI X1400 running in XGL on my laptop i gave up and instead i use Gkrellm it works and its easy setup but not nearly as complex.

---

### Post by Raavea on 2007-06-04
I'd like to see this too. And a guide to using conky themes. :P

 As for me, I'm using Fluxbox on a server install of Feisty, so all I had to do was install Conky from Synaptic and then open Conky up. It's bare bones and pretty ugly right now, though.

---

### Post by eentonig on 2007-06-04
Search the forum or web for ".conkyrc"

These are the 'configuration' files. Copy one of those in you home folder and start the program to see if you like the output. If you don't, move ity to a temp folder and try another.

Once you get an almost as you like config. Remove the things you don't want and put in stuff from the other examples you've downloaded and liked. That's how I did it.

Ps. You can have multiple conkies running, as long as they have different names for the .conkyrc file. (This is the default. If you use another name, you need to pass it at the conky command with an option)


For completeness, I included the install command as well
> sudo apt-get install conky
cp .conkyrc ~/.conkyrc
conkyrc &

---

### Post by Seisen on 2007-06-04
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

---

### Post by notwen on 2007-06-04
Here are two threads you might find useful.

[Compiling conky from source]("http://ubuntuforums.org/showthread.php?t=353362")

[Post your .conkyrc]("http://ubuntuforums.org/showthread.php?t=281865")

---

