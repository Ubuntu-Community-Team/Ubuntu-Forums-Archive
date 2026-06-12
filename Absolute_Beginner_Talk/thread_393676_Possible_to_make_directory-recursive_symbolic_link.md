---
title: "Possible to make directory-recursive symbolic links?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by DeadAmaranth on 2007-03-26
Ok, I got excited when I figured out how to do symbolic links. I mean, how to do them in the console as well as through the gui, anyway. Very useful command. Especially for saving space!

My situation is this:

I have Linux installed on an IDE drive, and my old XP install on  SATA.  I am finding myself spending all my time in Linux now. Soon enough I imagine I will re-format the SATA drive to make more room for Linux (yep, getting closer to the switch. Yay!).

In the meantime, I would like to use my SATA drive as a read-only storage point, to allow me to maximize the space on my /home partition. I already have the entire SATA drive symlinked under my ~/ directory. What I wonder is, could I somehow do a mass, recursive symlink operation to every folder, every file?

Let me try to clarify. I would like my ~/ folder to have basically a "mirror" quality, so that I no longer have to browse manually to my SATA drive to listen to music, or check out avi files, etc, etc.

I know I can do it manually, one file/folder at a time.... but... well, we're talking about MANY repetitions, considering how many files that is!

Can ln -s take a recursive argument/option? "man ln" and "info ln" don't seem to answer this, or else I'm reading it wrong. The third and fourth methods (listed in man/info) seem related to what I want, but... I'm still new at this. :)

---

### Post by Bachstelze on 2007-03-26
Well, obviously if you make a symlink for a dir, you will be able to access the dir structure as well. For example if you have /media/windows/foo and /media/windows/bar and you do

```
cd && ln -s /media/windows
```

You will be able to navigate the dir from ~/windows, so you'll have ~/windows/foo and ~/windows/bar

---

### Post by DeadAmaranth on 2007-03-26
Now that you've responded, I see the foolishness of my question. What bizarre thoughts which run through my mind sometimes! No need to complicate things. Sorry. :)

Still, I don't quite understand your code.

What does "cd &&" do?

Doesn't the && operator tell the shell to run one command, followed by another?

Wouldn't "cd" by itself do nothing? *shrug* Still new to bash here, bear with me.

Oh. I see. Nothing beats testing the example out in the terminal, I guess. "cd" takes you to your ~/ directory. Even quicker than "cd ~/". I learned something! Thanks! :p

---

