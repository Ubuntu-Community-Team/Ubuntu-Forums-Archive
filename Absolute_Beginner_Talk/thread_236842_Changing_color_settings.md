---
title: "Changing color settings?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-08-15
I know that when running Windows there were different color settings. Things such as 16bit, 32 bit, etc.

Are these things present in Ubuntu too? How would I go about finding out what mine is currently set at? How would I change it? Would I ever even need to change it?

Sorry, some things are still very confusing to me.

---

### Post by LadyDoor on 2006-08-18
Unless I'm mistaken, you're going to need to fiddle in your xorg.conf file. BE VERY CAREFUL and please read the whole post before you do ANYTHING. Even then something could go wrong. BE CAREFUL.

First, let's back it up. Twice. Fire up a terminal and copy/paste what comes after the dollar signs!

```

$ cd /etc/X11
$ sudo cp xorg.conf xorg.conf.bak
$ cp xorg.conf ~/xorg.conf.bak

```

Now, fire up your favorite text editor. I'll use nano--and if you do you nano, be sure to keep the "-w"! That makes sure it doesn't break up any lines.

```
$ sudo nano -w xorg.conf
```

Now, find the line that says **Section "Screen"**. I believe **control-w** (I'm going to start abbreviating "control-key" to **C-key**) is the "find" function.

A few lines below that, there should be a line that reads

```
DefaultDepth   16
```

Replace the number that comes after that with the number you want, press C-o to save the file, press C-x to save, and then restart the Xserver like so:

**control+alt+backspace**

It *should* come up with the proper color depth. Otherwise, you just **temporarily** broke X and are staring at a commandline. Here's how to fix it:

Remember those backups you made? We're going to use them. Log in, if necessary, and then do the following:

```

$ cd /etc/X11
$ sudo cp xorg.conf.bak xorg.conf
$ sudo reboot

```

That should fix it.

I hope that helps! Let me know!

--Door

---

