---
title: "Acer Aspire 5720"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by xRes on 2008-01-05
Hello,
I have seen the article relating to my laptop
[https://wiki.ubuntu.com/LaptopTestin...AcerAspire5720]("https://wiki.ubuntu.com/LaptopTestin...AcerAspire5720")
But am not 100% sure how to do what it asks when talking about setting up the sound and compiz so could someone please help me and explain before I go ahead and install
for example i dont understand how to get compiz to work. the guide talks about invoking it with script in the gnome session manager but i dont know how:


> To get Compiz-fusion working, you need to invoke it like this:

SKIP_CHECKS=yes compiz --replace

You can create a little script and put invoke it with the gnome session manager.

appologies for my noobishness

Thanks is advance,
xRes

---

### Post by xRes on 2008-01-08
Anyone??
Pretty please with flowers on top :)

---

### Post by magnat2 on 2008-01-22
> **xRes said:**
> Anyone??
Pretty please with flowers on top :)
Open the terminal and write:

& mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

And your problem is solved, when you want you cant turn the desktop effects in appearance settings:)

For any doubts try this: 

[http://acer5720linuxubuntu.blogspot.com/](http://acer5720linuxubuntu.blogspot.com/)

---

### Post by PriceChild on 2008-01-22
By the way, compizfusion will be blacklisted on your laptop for a reason.

You'll probably experience problems with video playback and effects.

---

