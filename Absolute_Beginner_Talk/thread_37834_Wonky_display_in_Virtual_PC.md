---
title: "Wonky display in Virtual PC"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by dots on 2005-05-28
Hello, how do you do?

Firstly, I must state how wonderful installing Ubuntu was: so brilliantly easy.

Under Virtual PC on Mac OS X, my Gnome display is quite distorted, and I was hoping that someone may be able to help me fix this little issue. A picture speaks a thousand words, so here is a screenshot of my desktop:

[Screenshot](http://solipsism.cc/zero/ubuntu.png) ([http://solipsism.cc/zero/ubuntu.png](http://solipsism.cc/zero/ubuntu.png))

I have Virtual PC set to 32Mb of VRAM, and I've installed the Nvidia drivers per the instructions in the guide.

Would anyone be able to offer me assistance? I would certainly appreciate it!

---

### Post by TravisNewman on 2005-05-28
you'll have to do the following:
ctrl+alt+F1, to get to a text console
sudo nano /etc/X11/xorg.conf

go down to the section for display modes and set the default display mode to 16bits, or delete the 24 bit color modes. 

Virtual PC can only do 16 bit color.

---

### Post by dots on 2005-05-29
Absolutely perfect, thank you so much!

---

