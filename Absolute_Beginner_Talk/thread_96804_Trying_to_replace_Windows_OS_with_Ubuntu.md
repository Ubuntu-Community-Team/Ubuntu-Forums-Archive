---
title: "Trying to replace Windows OS with Ubuntu"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by jbueler on 2005-11-29
I need help with a couple things. There are a few issues i am having with the ubuntu...

1. I cannot get my exteral usb hard drive to work correctly.
2. I don't know how to compile and install applications that I download
3. I have a dual monitor setup that uses an accelerated graphics card and a pci graphics card, how do I get both to work?


yeah i think that is a good start that will at least let me get rid of my windows box for the most part...

Any help i can get is appreciated..
Thanks
~jbueler~:confused:

---

### Post by MrFahrenheit on 2005-11-29
[QUOTE=jbueler]2. I don't know how to compile and install applications that I download[/QUOTE]


in case you weren't aware, most of the time, you don't need to compile applications yourself.  you can use apt-get from the command line or Synaptic to install applications.

---

### Post by natman on 2005-11-29
I think i may know how to help with 1)
when i tried and failed to use my usb memory stick, and eventually got it working by updating my BIOS. and that did the trick.

---

### Post by x__dark on 2005-11-29
[QUOTE=jbueler]I need help with a couple things. There are a few issues i am having with the ubuntu...

1. I cannot get my exteral usb hard drive to work correctly.
2. I don't know how to compile and install applications that I download
3. I have a dual monitor setup that uses an accelerated graphics card and a pci graphics card, how do I get both to work?


yeah i think that is a good start that will at least let me get rid of my windows box for the most part...

Any help i can get is appreciated..
Thanks
~jbueler~:confused:[/QUOTE]

For the first one, you need to mount it. Depending on the file system (most likely fat32 or fat16) you may or may not be able to move the files over from it.

The second, use apt-get.

The third, you'll need the linux driver for both or them, but if you have a semi-modern AGP card you should be able to just use that one for both. Seeing as Nvidia and ATI are the biggest distributors, i would check that out.

---

### Post by jbueler on 2005-11-29
hmm ok thanks that at least gives me a place to start... 
thanks

---

