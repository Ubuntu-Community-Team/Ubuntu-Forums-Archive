---
title: "What does -this- mean?  (Audacity download)"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Permanent Beginner on 2007-07-26
So I'm at what I think is the Audacity download page, and there's a list of "other packages related to Audacity".  

What in the world does -that- mean?

Does it mean that if I press the "download" button they'll come along too, or does it mean "Ha ha, sucker, now try and find these?"

PB

[http://packages.ubuntu.com/feisty/sound/audacity](http://packages.ubuntu.com/feisty/sound/audacity)

---

### Post by marco123 on 2007-07-26
Just go into add/remove programs in the applications menu (top left) search for audacity then check the box next to it and hit apply.

---

### Post by ThrobbingBrain66 on 2007-07-26
The packages with the red dot next to them are dependencies.  These packages MUST be installed along with audacity for it to work.

The green diamond and blue square are packages that aren't necessary for Audacity to work, but they add more functionality.

You'd be better off installing Audacity through the repos.  If you install it your way you could run into dependency hell.

Something like:
```
sudo apt-get install audacity
``` will pull in all the necessary packages.

---

### Post by zanglang on 2007-07-26
The "other packages" are dependencies for Audacity and other suggested ad recommended packages related to Audacity. If you click Download you'll pretty much only get the Audacity .deb, but if any dependencies exist in Ubuntu (well in this case they all do) apt will automatically download and install them for you as well.

Edit: ThrobbingBrain66 summarizes it pretty well. :D

---

### Post by SPRL on 2007-07-26
Just a note: to remember to right click the vol. icon on the panel and tweak the levels. When I first installed Audacity it would not rec. until I moved some levels.:)

---

### Post by Permanent Beginner on 2007-07-26
"
You'd be better off installing Audacity through the repos. If you install it your way you could run into dependency hell.

Something like:
Code:

sudo apt-get install audacity

will pull in all the necessary packages.

  "

*************

Thank you for the clear and useful reply!!  I've never done that yet but it's probably figureoutable.

I sure wish that there were some kind of committee that took questions like this and fixed the pages so that the ambiguity causing the question were resolved.

I also wish that Tanya Roberts liked to hang around with me.

PB

---

### Post by Permanent Beginner on 2007-07-28
> **ThrobbingBrain66 said:**
> The packages with the red dot next to them are dependencies.  These packages MUST be installed along with audacity for it to work.

The green diamond and blue square are packages that aren't necessary for Audacity to work, but they add more functionality.

You'd be better off installing Audacity through the repos.  If you install it your way you could run into dependency hell.

Something like:
```
sudo apt-get install audacity
``` will pull in all the necessary packages.

Well, I tried that today and like pretty much everything else I've done so far, it didn't work.
A message came back saying 

Reading package lists... done
Building dependency tree
Reading state information... done
E:  Couldn't find package audacity

So now what?

PB

---

### Post by por100pre1 on 2007-07-28
> **Permanent Beginner said:**
> Well, I tried that today and like pretty much everything else I've done so far, it didn't work.
A message came back saying 

Reading package lists... done
Building dependency tree
Reading state information... done
E:  Couldn't find package audacity

So now what?

PB

Weird, that should have worked. Check In System> Administration> Software Properties. Under Ubuntu software tab check everything except source code.

---

### Post by Permanent Beginner on 2007-07-28
I'd be happy to, but there -isn't- a System > Administration > Software Properties.
There's a Software Sources, but no Properties.

PB

---

### Post by Permanent Beginner on 2007-07-28
Oh, wait, this Sources might be what you mean, there is a list of things checked including an unchecked "Source Code"...that's that way.

PB

---

### Post by por100pre1 on 2007-07-28
It should be everything other than source code. Don't check Source Code. Sorry for the mistake I'm using Ubuntu in Spanish.

---

### Post by por100pre1 on 2007-07-28
Forgot to say you can also change there which server to use. After using it should ask you to reload your sources.

You can also do it from terminal:

```
sudo apt-get update
```

then try to install Audacity again:

```
sudo apt-get install audacity
```

Let us know what you get...

---

