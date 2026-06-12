---
title: "loading new software on 2 computers"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by jeffbilling on 2007-10-19
I have a computer at home which I use to download programs via internet.
I use 'Add/Remove' or 'Synaptic Package Manager' to do this.
I want to put the 'Gcompris' suite of software on a second computer at a school site, but it does not have access to the internet.
 (I anticipate that I will also want to add other programs as I develop the school site)
Is there any way I can do this. 
:)

---

### Post by Dr Small on 2007-10-19
You could try:
```
sudo apt-get install -d *packagename*
```
And that will download the actual debian and not install it; Giving you a file that you can put on a flash drive and transport to the school computer.

But this probably does not download dependencies, and most likely will not install or work properely on the school computer without the dependencies.

Dr Small

---

