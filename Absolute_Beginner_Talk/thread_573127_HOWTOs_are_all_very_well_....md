---
title: "HOWTOs are all very well ..."
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by rug77 on 2007-10-11
While I've made use of many (too many really) helpful posts to finally get windows which wobble when wiggled, I don't really know how I've done it.  Is there some information source that will tell me what it actually means when I edit a file to say screen :1 in stead of screen :0 or whatever ?

Copying something that works (after having copied many other somethings that didn't quite make it ...) doesn't give me any understanding, and I'm interested to know what's going on.  It's what many people cite as one of the major benefits of choosing Linux after all.

While I'm here, and having got that somewhat nebulous request for everyone to provide helpful information rather than just answers that work (for which I remain grateful), I have a more specific question.

I've seen the funky videos of windows being minimised with a sort of wiggly diminution into the task bar.  I've been into the manager, and tried changing the minimise animation.  No change.  Too many years of Windows has me looking for a button with Apply on it, but no such thing to be seen.  How do I change the look using the Compiz managing tool ?

Thanks ...

Matt

---

### Post by hyper_ch on 2007-10-11
if the howto contains copy'n'paste code to put in a terminal you can find out very easly by using the man pages...

e.g.

```

sudo rm -Rf /tmp/downloads

```

There are two commands in there:
- sudo
- rm

What do they do? Look it up in your man pages:

```

man sudo

```

(use arrow keys and page up/down keys to navigate and "q" to exit)

and

```

man rm

```

That should give you information to any cli program.

---

### Post by Hospadar on 2007-10-11
Configuration files are kind of a beast of their own, as every application uses different formats and conventions.  You can always look for specific documentation for the application you are using.

Also, reading up on the linux filesystem and basic architecture, as well as learning about the /etc/X11/xorg.conf file (and xorg in general) as well as learning about commands like "lspci" "lsusb" "ifconfig" will probably really help you pick out important stuff.  There's plenty of info on all this kind of stuff with a little googling

And as said above, if you get some commands in a howto that you don't understand, you should "man" them so you know what's going on.

---

### Post by rug77 on 2007-10-11
> **Hospadar said:**
> Configuration files are kind of a beast of their own, as every application uses different formats and conventions. 

That's kind of what I was driving at.  It would be more useful to have a short piece saying 'Enter the following lines in such-and-such file.  This will enable the widget, and set the doodad to use the wotnot, rather than the default ...'

You're right, I could trace info about all the configuration files I am blindly copying and pasting stuff into, but then I would be looking at loads of technical stuff, searching for the tiny part that relates to what I have changed.

I guess it will come in time though.

On my second question, how do I change the behaviour ?  I can change the 'minimise window' animation from 'Magic Lamp 1' to 'Explode (3d)', but no change to the minimise behaviour at all.

How do I make these changes ?  Surely this is a very simple question, with a very simple answer ?

Help please ?

Matt

---

### Post by hyper_ch on 2007-10-11
> **rug77 said:**
> That's kind of what I was driving at.  It would be more useful to have a short piece saying 'Enter the following lines in such-and-such file.  This will enable the widget, and set the doodad to use the wotnot, rather than the default ...'


I disagree... by just giving directions you have a quick fix... however if you want to know how it works, you're free to do research or ask.

---

