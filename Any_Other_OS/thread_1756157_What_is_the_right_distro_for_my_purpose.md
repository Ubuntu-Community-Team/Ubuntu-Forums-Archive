---
title: "What is the right distro for my purpose"
date: 2011-05-11
forum: Any Other OS
---

### Post by ClientAlive on 2011-05-11
Hi,

I've been thinking about migrating my o/s (Ubuntu 10.04) to a virtaul machine. I would be using Oracle Virtual Box to run it in.

My question is:

What is a very minimal linux distro that virtual box could be run on top of. In other words, to use as the host o/s.

More specifically. I don't need it to have a gui and would even like to strip out anything that is not absolutely necessary for it's own maintenance and running/ supporting virtual box. I'm not even sure I need much of a home directroy except maybe on folder in it to use as a shared folder between it and virtual box (not even sure that would be needed. It would need to be stable and reliable though - and, I think, virtual box seems to like debian based stuff? Anyway . . .

I've never done it before but I am willing to compile something myself. In fact, doing that even sounds like a kind of fun project.

Can anyone suggest what components the right components I would need to compile what I need to end up with? In the end what would I want to end up with? What would that picture look like?

Thanks

---

### Post by jeffathehutt on 2011-05-11
Personally if I was going to attempt a project like that, I would start with a minimal install of debian stable and a simple window manager / desktop like openbox or lxde.  That way, you start with a nice, stable base system that won't need constant updating.  Also, a minimal install shouldn't use too much RAM, allowing you to dedicate more RAM to the virtual machine.

If you also want to compile things, it's usually pretty simple.  Most programs use the standard
```
./configure
make
make install
```

**./configure** allows you to specify which options you want in the program, **make** will do the actual compiling, then **make install** will copy the files to their proper place in the system.

---

### Post by Allavona on 2011-05-12
Would TinyCore work for that purpose?

---

### Post by Rubi1200 on 2011-05-12
I think this post from forum member Fraoch might also interest you:
[http://ubuntuforums.org/showpost.php?p=10758005&postcount=20](http://ubuntuforums.org/showpost.php?p=10758005&postcount=20)

---

### Post by Spice Weasel on 2011-05-12
> **jeffathehutt said:**
> Personally if I was going to attempt a project like that, I would start with a minimal install of debian stable and a simple window manager / desktop like openbox or lxde.

If you were just running one application, there would be no reason to even have a window manager installed. Just X would do.

---

### Post by ClientAlive on 2011-05-12
Thank God. You guys totally get it. One guy talks about stability and minimal (in the same sentance I think), another talks about not even needing an window manager (what a glorious thought, oh my), and someone else says, "Tiny Core."

This is the third thread of this nature I have started and we're right on target. Plain jane, nothing special, nothing wasted; but very stable, secure and serves the one purpose it is intended for - running virtual box.

It's just that I was also finding my way when I made the other threads so really they are perfectly on target too. I'm so thrilled!

Thanks a bunch guys.


> **Allavona said:**
> Would TinyCore work for that purpose?

It's pretty cool that it's only 10 mb. It could work - except I'm pretty sure (read: basically committed) that I want to do my own build. It's just an experience I want to have in life. And I think it's the best way to end up with something tailored to exactly my needs.


> **jeffathehutt said:**
> Personally if I was going to attempt a project like that, I would start with a minimal install of debian stable and a simple window manager / desktop like openbox or lxde.  That way, you start with a nice, stable base system that won't need constant updating.  Also, a minimal install shouldn't use too much RAM, allowing you to dedicate more RAM to the virtual machine.

If you also want to compile things, it's usually pretty simple.  Most programs use the standard
```
./configure
make
make install
```

**./configure** allows you to specify which options you want in the program, **make** will do the actual compiling, then **make install** will copy the files to their proper place in the system.

So is a 'minimal install' just a selection you make during the installation process or is it it's own release?

If I wanted to make my own build what are the basic pieces that need to go into it? I'm going to take a guess here, ok?

~ A kernel
~ Patches
~ Maybe updates (but I'd think you do that last after everything is complete and operational)
~ What about bash? Is it already in the kernel or is it it's own package?
~ What about updates? Is there already something in the kernel or it's it's own package? Or do I have to go in and type "sudo apt-get update" and "sudo apt-get upgrade" (or maybe "su") every day? And how do I keep it from installing things I don't want added?
~ The thing that actually draws the window? I mean the bare bones just draws the window and makes it so you can move the window within the screen.

Ok, not much of a 'guess' I guess :D  When I think of this though, that's what comes into mind.


> **Spice Weasel said:**
> If you were just running one application, there would be no reason to even have a window manager installed. Just X would do.

This reminds me of a discussion I had with someone a few weeks back. I had asked about x and window managers and desktop environments. I was trying to understand how they work together and also what each one does. It came up that perhaps a window manager was not exactly mandatory (or was that the desktop manager?). I don't recall. In any case, the person who was talking with me mentioned that they had set things up so they weren't using a window manager (or something like that). That they were just using x only. He did say it took a little work to get it 'to work'.


> **Rubi1200 said:**
> I think this post from forum member Fraoch might also interest you:
[http://ubuntuforums.org/showpost.php?p=10758005&postcount=20](http://ubuntuforums.org/showpost.php?p=10758005&postcount=20)

It certainly does. Very informative. Thank you.

---

### Post by Allavona on 2011-05-12
I'm glad you want to do your own build. Let me know how it turns out!

---

### Post by ClientAlive on 2011-05-12
> **Allavona said:**
> I'm glad you want to do your own build. Let me know how it turns out!


Absolutely!

---

### Post by lykwydchykyn on 2011-05-12
> **ClientAlive said:**
> 
So is a 'minimal install' just a selection you make during the installation process or is it it's own release?

If I wanted to make my own build what are the basic pieces that need to go into it? I'm going to take a guess here, ok?

~ A kernel
~ Patches
~ Maybe updates (but I'd think you do that last after everything is complete and operational)
~ What about bash? Is it already in the kernel or is it it's own package?
~ What about updates? Is there already something in the kernel or it's it's own package? Or do I have to go in and type "sudo apt-get update" and "sudo apt-get upgrade" (or maybe "su") every day? And how do I keep it from installing things I don't want added?
~ The thing that actually draws the window? I mean the bare bones just draws the window and makes it so you can move the window within the screen.

Ok, not much of a 'guess' I guess :D  When I think of this though, that's what comes into mind.





Looks like you need to check out "Linux from scratch" [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Otherwise, a minimal install of debian without X is about 600 Mb last time I checked.

Virtualbox may require a window manager to actually achieve full screen, but that can be tested.  Of course, if you can EVER imagine a situation where the non-virtualized OS will be presenting you with more than one window, you want a window manager.  Good news is that there are umpteen lighter-than-light window managers to choose from.

Virtualbox will have some dependencies of its own, I believe the GUI is written in Qt4, though that may be bundled.  Frankly, this will be a lot easier starting with a minimal install (read: CLI only) of some mainstream distro like Debian or Ubuntu rather than starting from bare metal and compiling everything.  There are a lot of non-obvious things that make up a Linux system.


Tinycore might work, but you'd probably want to trade it's default Xvesa for an actual Xorg install, and I don't know for sure how virtualbox will react with its kernel.  Worth a try, I guess.

---

### Post by jeffathehutt on 2011-05-12
> **ClientAlive said:**
> 
This reminds me of a discussion I had with someone a few weeks back. I had asked about x and window managers and desktop environments. I was trying to understand how they work together and also what each one does. It came up that perhaps a window manager was not exactly mandatory (or was that the desktop manager?). I don't recall. In any case, the person who was talking with me mentioned that they had set things up so they weren't using a window manager (or something like that). That they were just using x only. He did say it took a little work to get it 'to work'.


X is what actually draws the screen.  It is the most basic level that you can easily interact with.

Window managers are the programs that draw the window borders, and allows you to move windows around on the screen.  Also, the window manager controls placement and sizes.  Examples include Openbox, Fluxbox, Awesome, wmii, and others.

A desktop environment is just a collection of useful, often integrated software that gives you the 'complete' experience.  Examples include Gnome, KDE, Xfce, and Lxde.  Take Lxde for example.  It is just openbox, along with software that makes it more useful to some, like a panel (lxpanel), terminal (lxterminal), a file manager (pcmanfm) and others.

---

### Post by Spice Weasel on 2011-05-13
If you have a bit of spare time, watch [these]("http://www.youtube.com/watch?v=tvbAawBGmgE") to learn more about X11 and its role in your system.

---

### Post by ClientAlive on 2011-05-13
> **Spice Weasel said:**
> If you have a bit of spare time, watch [these]("http://www.youtube.com/watch?v=tvbAawBGmgE") to learn more about X11 and its role in your system.


Oh, absolutely I'll be watching those. Thank you.

---

### Post by ClientAlive on 2011-05-13
Oh-My-God . .. Thank you thank you thank you. I'm sitting here watching these videos literally with tears in my eyes. The sheer quantity of understanding this person conveys is indescribable. I wish everyone would instruct in this way. Perhaps dull and boring for the initiated but absolutely integral for those who aren't.

God bless you my friend.

---

### Post by ClientAlive on 2011-05-14
Well, looks like I have some research to do. Thanks a bunch for all the great info and leads guys.

Jake

---

