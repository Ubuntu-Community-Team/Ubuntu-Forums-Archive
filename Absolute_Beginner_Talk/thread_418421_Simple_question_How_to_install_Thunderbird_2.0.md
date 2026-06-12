---
title: "Simple question: How to install Thunderbird 2.0?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by qix on 2007-04-22
Hey

The title more or less says it all. I downloaded Thunderbird 2.0 from official site, for linux. But what is it I have downloaded? It's not source-code as far as I can see, but it's not an install script either? Or?
Do I just need to extract the file to someplace and run it without installing?

I just don't know what it is I have downloaded, or how I install it properly. The documentation that followed the package is next to non-existent... I couldn't find any informative stuff at least.

---

### Post by Martje_001 on 2007-04-22
You can install it by: Applications --> install/remove
Then search for Thunderbird

You can also do it via the terminal by typing: sudo aptitude install thunderbird

---

### Post by adam_kimber on 2007-04-22
Just extract the gzipped tarball to a directory of choice. I have made a directory called "bin" in my home directory for executables that are not installed using Synaptic or apt. 

After extraction double click on "Thunderbird", the icon will look like a command prompt. 

After that select run and Thunderbird will run. You can create a launcher to point to this file to stop it asking to run if  you wish.

---

### Post by Kobalt on 2007-04-22
> **Martje_001 said:**
> You can install it by: Applications --> install/remove
Then search for Thunderbird

You can also do it via the terminal by typing: sudo aptitude install thunderbird
Thunderbird 2 is not out yet, it's not in the repos yet either.

You can run it by double clicking on the "thunderbird" file, pick Launch, and here you go...

---

### Post by qix on 2007-04-22
Okay thanks. Where is the default place to install such programs? /usr/bin or? I mean if it aint in your home directory.

---

