---
title: "Confusion regarding compiling and other programming woes"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Dudemanguy on 2006-07-23
I'm totally new to Linux, and fairly new to programming. I've done a little VBasic ages ago and I know python fairly well. For the past day or so I've been trying to figure out how to use IDLE in Linux, as well as all of these other compilers (or something, I'm not positive if I know all the lingo properly). The languages I primarily care about using are Python, C++, and Java, so could anyone help me just figure out how to do anything?

---

### Post by mlind on 2006-07-23
Python related stuff is installed by default. For a C and C++ compiler install package called build-essential. There's a programming sub-forum here that could suit better for this thread.
For Java, I suggest some easy-to-use IDE, like NetBeans or Eclipse to get you started.

Maybe searching existing threads on programming forums can get you started better.

---

### Post by Dudemanguy on 2006-07-23
Hm, that sort of helped, but sort of not. I'm not so much trying to figure out what to use as I am trying to figure out how to open what I have. Like, I know if I type python into the terminal, I get python, but I can't actually write scripts in there or do anything besides really simple things there as far as I know. What I want to do is open up the main program, or figure out a way to compile stuff.

I would have posted this in the programming section, but it seemed more like a lack of technical Linux-using skill than a lack of programming skill.

---

### Post by maruchan on 2006-07-23
> What I want to do is open up the main program, or figure out a way to compile stuff.

By "main program," it sounds like you want an IDE, but maybe (I'm guessing, sorry) you didn't know this:

The program "python" doesn't have a GUI. Normally you run an "IDE" or Integrated Development Environment program like Anjuta (for Python) or SciTE. These programs have a GUI (like a word processor for programming) and you configure them to run Python with your python program as input when you press something like a "run" (or compile) button.

Anyway, the same applies for Java, C compilers, etc. They let IDEs do the GUI work :)

Edit: Here are some screenshots of Anjuta; is this the sort of program you're looking for?

[http://anjuta.sourceforge.net/screen-shots](http://anjuta.sourceforge.net/screen-shots)

Gambas is another IDE that's easy to use (it's BASIC-based):

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

---

### Post by Dudemanguy on 2006-07-23
I just tried installing anjuta, and when i do the ./configure step, there's an error about:

"""
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
"""

I haven't been able to sucessfully install anything on this system thus far, and I think it's because I'm using the AMD64 architechture version (since I have that). If I were to use the i386, would it cause any reverse compatability incompatabilities (since I don't have anything saved on this yet)? And is that a well suggested course of action?

Edit: Also, isn't IDLE and IDE for Python? That's what I've always used on windows, though I may just be getting things confused. I checked in add/remove programs, and it was there, but I have no clue how to get to it.

---

### Post by maruchan on 2006-07-23
:-k Mind if I ask why you're compiling? Most users would:

1. Open Synaptic: Alt+F2, type "gksudo synaptic" and give it your admin password so you can install stuff
2. search for "Anjuta," 
3. right-click the item and mark it for install, 
4. and click "Apply."

After that it should appear in your GNOME menu.

Edit: Video: [http://video.google.com/videoplay?docid=5253052326994067125](http://video.google.com/videoplay?docid=5253052326994067125)

---

### Post by Dudemanguy on 2006-07-23
Oh wow this is confusing. I'm in the synaptic package manager now, but I can't find Anjuta even after searching for it. I'm not sure if I quite understand how it works either.

And is the GNOME menu the linux version of the task bar?

Edit: I'm watching the video, and I saw how they did it, but I didn't see anything named Anjuta when I searched for name and description. I did see:

devhelp
devhelp-common
livdevhelp-1-0
livdevhelp-1-dev

---

### Post by Dancingwllamas on 2006-07-23
You may need to enable the Universe and Multiverse portions of the Ubuntu repositories.

Open Synaptic, then choose settings>repositories. One of the entries should say "Ubuntu 6.06 LTS (Binary)". Highlight it, then click the "Edit" button. Select the check boxes. Close the menus and reload synaptic.

---

### Post by Dudemanguy on 2006-07-23
Oh wow thanks alot, that got the job done. Yes, thank you all a lot for the help, I'm off to enjoy my new treasures.

---

### Post by Dancingwllamas on 2006-07-24
Glad it worked out. :)

---

