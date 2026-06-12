---
title: "Problem with Gogh"
date: 2007-12-21
forum: Art &amp; Design
---

### Post by Azraelthe7th on 2007-12-21
I've installed Gogh on my AMD64 Ubuntu Gutsy, and whenever I try to draw something, the cursor would disappear and lose any responsiveness.  I've included a video file of the problem to illustrate what's going on.  I've checked to make sure I have all the Python scripts, and it appears I may be missing the PyXML.  Unfortunately, I can't seem to find it.  Any ideas?

[ATTACH]53938[/ATTACH]

---

### Post by Azraelthe7th on 2007-12-23
*bump* Any help?  Please?

---

### Post by Azraelthe7th on 2007-12-29
I've noticed there's been 70 views, but no answer.  I take it there's no way around it?

---

### Post by Azraelthe7th on 2008-01-18
The project's website is down, and I still haven't heard from the guy who made the program.  I guess it's a dead end.

---

### Post by Paul820 on 2008-01-18
pyXML is available on sourceforge as source code [http://pyxml.sourceforge.net/]("http://pyxml.sourceforge.net/")

---

### Post by Azraelthe7th on 2008-01-18
Thanks, but I'm still relatively new with Ubuntu (been using it for a few months now), so I'm still not 100% sure of how I would do this without screwing something else up.  Care to help?

EDIT: Ok, tried installing it with the guidelines in the README file, but still nothing.  :(

---

### Post by Paul820 on 2008-01-18
Yes i will help you. Do you have **build-essential** installed? I would think you need the package **python-dev** available through synaptic if you have not already got it.
From the readme file:
> The only requirements for installing the package are Python 2.0 or
later, and a C compiler. Note that the Python must actually be an
INSTALLed python, rather than one that is being used directly from
Python's build area. This release has been tested with Python 2.x.

Then make sure you are inside the folder and from the terminal type:
> python setup.py build
and then
> sudo python setup.py install

Try that and then let me know what happens for you. I just did it and it built and installed for me.

---

### Post by Azraelthe7th on 2008-01-18
I already have the **build-essential** package installed, and I installed the py-xml script, and still no go.

I also tried using force-architecture on the .deb package found on get-deb, in case I'd have more luck with a 32-bit build, and it said I was missing python-lxml.  I tried installing that too and still nothing.

---

### Post by Paul820 on 2008-01-18
I see what you mean, i have just installed the 64bit version off getdeb,net and it asked me if i wanted to install py-lxml so i said yes and even though i have py-xml installed it does exactly the same as you said, the cursor disappears. So i don't know what could be wrong with it. The website being down doesn't help the situation either.

---

### Post by Azraelthe7th on 2008-01-19
Well, thanks for the help anyway.  I'll still look around to see if there's a fix for this, or if we'll have to wait for the author's return from wherever.

---

