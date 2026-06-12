---
title: "flash problems"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by witham on 2007-07-22
I have downloaded and installed today flash player for linux from macromedia's website but everytime I try and load a flash game or movie firefox either closes or greys out and I have to force a close?
The installation seemed to go fine from the terminal window so I am at a bit of a loss and any help would be appreciated.

---

### Post by happy-and-lost on 2007-07-22
Does your machine have an onboard Intel graphics chip (865G or similar)? If it does, check xorg.conf. Check that the default colour depth is set to 24, not 16. Flash dies at 16 colour depth.

---

### Post by witham on 2007-07-22
Flash used to run on this machine when it ran Windows XP?

Anyway I did type in xorg.conf into the terminal and it didn't recognise the command so I guess I misunderstood you.
I then went into device manager and looked at the graphics card and it didn't list xorg so could you please spell out for me if you have the time where I need to look!

---

### Post by stmiller on 2007-07-22
witham: you can do this to confirm that flash installed ok:

type 

```

about:plugins

```

in the Firefox address bar and hit enter. Let us know if flash is listed.

---

### Post by bob scott on 2007-07-22
Witham I hope u don't mine me butting in but I have the same problem.  I did post but still have no solution.
Stmiller I did what u said  and discovered that the plugin did not install.  But I ran the synaptic package manager!   If you can help me while helping Wiitham I would be thankful.  I have a  four year old sony vaio with  Pentium Four.  I do have and updated grapics driver,  which allowed me to run Skype.

---

### Post by happy-and-lost on 2007-07-22
OK, into the terminal type:

*cat /etc/X11/xorg.conf*

And post back what it spits out.

---

### Post by bob scott on 2007-07-22
here is what i had:

bob@bob-laptop:~$ cat/etc/Xii/xorg.conf
bash: cat/etc/X11/xorg.conf:   No such file or directory

---

### Post by happy-and-lost on 2007-07-22
There should be a space between cat and /etc/X11/xorg.conf

---

### Post by bob scott on 2007-07-22
I got about 5 pages of info.   mainly this is a "xorg X Window System server configuration file"

---

### Post by happy-and-lost on 2007-07-22
Yes. That's what we want to see.

---

### Post by bob scott on 2007-07-22
Good.  But how do I get the flash plugin to install?   Remember, Synaptic Package Manager is not installing it.

---

### Post by happy-and-lost on 2007-07-22
I mean I want to see what your xorg.conf says, just to rule out the possibility of an incorrect colour depth.

---

### Post by bob scott on 2007-07-22
Here is what I see for the monitor:
Device                                   "Ati Technologies Inc   Radeon---
Monitor                                  "generic Monitor"
DefaultDepth                    1
Modes                               "1024x768
EndSubsection
Subsection "display"
Depht                                4
Modes                                "1024x768"

---

### Post by bob scott on 2007-07-22
there is more to the last post;

EndSubsection "Display"
depth                           8
MOdes                        "1024x768"
.
.
.
.
SubSubsection "Display"
Depth                           24
Modes                           "1024x768"
EndSubsection

Let me know if you need more

---

### Post by bob scott on 2007-07-22
I have determine that my default depth is 24.  so disregard my earlier post.

---

### Post by bob scott on 2007-07-22
I have solved my flash problem.  I used the post of Gremlinzzz.

---

