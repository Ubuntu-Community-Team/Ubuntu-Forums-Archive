---
title: "What exactly do I need?"
date: 2007-03-11
forum: Art &amp; Design
---

### Post by nikon07 on 2007-03-11
Ok here are my system specs:
AMD Athlon 64 X@ Dual Core, NVIDIA GeForce 6150 LE.

I would like to know what I need to do for xcompmgr?
I have tried many times with 6.06 and beryl nothing doing there, so I upgraded to edgy 6.10.
PLEASE HELP!!!!!
Thanks in advance for any advice.

---

### Post by jem7v on 2007-03-11
This is a question that's probably better suited for the Desktop Environments part of the forum.

As for getting composite managers to run, it's definitely simpler in Edgy than it was in Dapper.  I haven't tried xcompmgr before... you'd probably have better luck finding support for Beryl or Compiz (and of the two, I'd recommend Compiz, because you don't see many "Help, my compiz broke!" threads, and there were 7 broken beryl threads in the Desktop Environments section yesterday morning).  [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) is a good starting point to learn more about them.

[http://doc.gwos.org/index.php/CompositeManagerGuide](http://doc.gwos.org/index.php/CompositeManagerGuide) has the only howto I've ever seen for xcompmgr, and it's pretty old (i.e., it was written for 5.10 Breezy Badger).  It may or may not work.

---

### Post by nikon07 on 2007-03-11
Thank you also do I need to install the xgl thing?

CompositeManager/Xgl,<------this?

I tried to run this in 6.06 and It crashed my graphics card, I'm a little leary of it 

Thanks

---

### Post by nikon07 on 2007-03-11
Ok I need help real fast PLEASE!!!!

I installed AIGLX/using this guide [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy")

once I typed this in 
```
sudo /etc/init.d/gdm restart

```

It took me to a black screen, and lke a huge Terminal, where I can enter code but I have nothing else.  How do I get back to my desktop enviroment???????   PLEASE HELP ME

---

### Post by jem7v on 2007-03-11
Did it give you any error messages about what happened?

You're right - not only is it Like a huge terminal, that's exactly what it is.  You could try logging in there and going back into your xorg.conf file and removing all the lines you put in there on the [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy) walkthrough, then restarting gdm again and seeing if that takes you back to where you started.

Don't forget that just as [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) says in its first sentence, this can be really buggy, unstable stuff.  Setting it up might be a breeze or it might be hell, depending on whether or not Zeus is in a good mood while you're doing it.

---

### Post by noen on 2007-03-12
Try this walk through:

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

In the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

From your description it sounds to me like this procedure would help. But read the walk through first so you know what to expect and to verify that it will help your situation. Lots of good info on his site.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

:)

---

