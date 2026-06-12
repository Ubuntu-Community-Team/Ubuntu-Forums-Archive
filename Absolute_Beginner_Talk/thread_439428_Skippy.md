---
title: "Skippy"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by hanuman1000 on 2007-05-10
hello

i want to use skippy with my ubuntu feisty with gnome, but it doesn't work. i installed it with synaptics but all i get it is:

WARNING: Couldn't load config file '/home/axel/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.


what does it mean?

is there an alt. to skippy that works good?

---

### Post by Foxmike on 2007-05-10
It looks like there is missing file.

Files names that begins with a dot (.) and end by "rc" usually are configuration files a program reads to find options etc.  Those files are usually held in you home directory ($HOME), which is the equivalent of the "My Documents" folder into Windows.

I don't have skippy installed at home and I am not at home, so I cannot give you any indice now on what should thil file contain.  However, you could try in a terminal:
```
touch /home/axel/.skippyrc
```

This will create the missing configuration file, but it will be empty, so it might not solve the problem, but it might solve it as well.

So after, try to open skippy again, from the terminal, I guess by typing

```
skippy
```

If it doesn't work, post back the result the terminal gave you, it will be easyer to help you!

Good luck!

-FM

---

### Post by hanuman1000 on 2007-05-10
thx for help!

this is what i get

WARNING: '/home/axel/.skippyrc' is empty.
WARNING: $HOME/.skippyrc not found loading default config.


guess its not supposed to be empty ;)

i downloaded it with Synaptics

---

### Post by Foxmike on 2007-05-10
Ok well as I am not in front of my Ubuntu computer, I make a look tonight when I'll get back home.  Good luck 'till then!  By the way, what is that program for?  Maybe is there an alternative?

Regards,

-FM

---

### Post by hanuman1000 on 2007-05-11
hi and thx for help!

Skippy is a program much alike Exposé for MacOS, where you press a key and all your active screens appear and you can chose between them. Beryl has the same effect, but that prg is too much and too heavy and too teenage for me...

---

### Post by thartono_cisco on 2007-06-05
Hi,
After you install skippy, the skippyrc file is located at /etc/X11/skippy/ , so you could copy the rc file to your home directory :

cp /etc/X11/skippy/skippyrc ~/.skippyrc

hope that helps,
Tony

---

### Post by process91 on 2007-08-13
The message below:

WARNING: Couldn't load config file '/home/mboratko/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.

Just means that you don't have any configuration file set, and it will use the default configuration instead. That's fine, it will still work. Just press F11 and it should show you all the windows tiled on the screen. Too bad it doesn't have an animated effect like OSX though...

---

