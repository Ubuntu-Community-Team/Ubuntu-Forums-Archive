---
title: "Synaptec vs Terminal"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by _Chris_ on 2006-05-02
This is certainly a 'newby' question, but I'm wondering if using the terminal to inststall a package, ie "sudo apt-get install xlibs" accomplishes the same thing as using Synaptec Package Manager to install a package by the same name.  Is Synaptec just the GUI method?

Thanks,
Chris

---

### Post by nanotube on 2006-05-02
yes, synaptic is just a gui frontend to apt-get. they accomplish the same thing. :)

---

### Post by _Chris_ on 2006-05-02
[QUOTE=nanotube]yes, synaptic is just a gui frontend to apt-get. they accomplish the same thing. :)[/QUOTE]

Great!  Thanks for your help Nanotube!

---

### Post by Jagot on 2006-05-02
When performing package management from the terminal, I prefer to use aptitude instead of apt-get.  The command you have to issue is almost identical.  Using the example you gave, it would be:

```
sudo aptitude install xlibs
```

Aptitude handles dependancy issues better than apt-get.

---

### Post by Borniet on 2006-05-02
One advantage of using Synaptic is that you can search for your packages in a user-friendly way.

---

### Post by jethro10 on 2006-05-02
[QUOTE=Borniet]One advantage of using Synaptic is that you can search for your packages in a user-friendly way.[/QUOTE]

I would totally agree, as a fairly newbiw myself, but an IT person with a fair amount of knowledge, I find a lot of help here is guided towards the command line, when its easily possible to do it with a graphical method.

I find it putting newbies off. It certainly makes my wife think linux is crap, however when we figure out the graphical way to do (most) things, were all happy again.

J

---

### Post by Tedd on 2006-05-02
I feel more comfortable with the command line, but that's just me.

---

### Post by Titus A Duxass on 2006-05-02
Searching in apt is also easy:

sudo apt-cache search ndis for example gives you everything that has the letters ndis contained in the title - ndiswrapper-utils, etc.

---

### Post by Borniet on 2006-05-02
[QUOTE=jethro10]I would totally agree, as a fairly newbiw myself, but an IT person with a fair amount of knowledge, I find a lot of help here is guided towards the command line, when its easily possible to do it with a graphical method.

I find it putting newbies off. It certainly makes my wife think linux is crap, however when we figure out the graphical way to do (most) things, were all happy again.

J[/QUOTE]
Totally agree with the wife thing
And we all know who is the boss at the end... ;-)

---

### Post by gr0kzer0 on 2006-05-02
Years of doing things the Windows/Mac way has gotten millions of computer users used to doing things through a GUI. So these people say it's easier to operate in a point-and-click environment, and are put off by the command line.

This is a great shame as all *nix systems are used to full capacity through the command line, as the GUI necessarily hides many features behind its simplified facade.

---

### Post by Borniet on 2006-05-02
[QUOTE=gr0kzer0]Years of doing things the Windows/Mac way has gotten millions of computer users used to doing things through a GUI. So these people say it's easier to operate in a point-and-click environment, and are put off by the command line.

This is a great shame as all *nix systems are used to full capacity through the command line, as the GUI necessarily hides many features behind its simplified facade.[/QUOTE]

I fully agree with this. However, there are some things to take into account:
1. My wife needs to work with this PC too... and she doesn't like the 'terminal way of life'.
2. Sometimes I don't need the full capacity of a terminal(-app), I just want to relax and click and browse.
 Don't misunderstand me, I always have at least one terminalwindow open (mostly even 1 per desktop, and a few extra floating around). But to non-IT'ers, or on a sunny day, I love my mouse too.

---

### Post by halfvolle melk on 2006-05-02
And the wiki shows how to use the GUI to some extend. However
> I find a lot of help here is guided towards the command line, when its easily possible to do it with a graphical method.
One reason for this is not per se that the CLI is better, but telling someone to do "sudo whatever" takes a lot less time than producing 5 screenshots with descriptiv information.

---

### Post by nanotube on 2006-05-02
[QUOTE=Jagot]When performing package management from the terminal, I prefer to use aptitude instead of apt-get.  The command you have to issue is almost identical.  Using the example you gave, it would be:

```
sudo aptitude install xlibs
```

Aptitude handles dependancy issues better than apt-get.[/QUOTE]
yea, aptitude is like the best thing since sliced bread. :) in fact, i don't know why they dont have aptitude be the default, instead of apt-get. 

but i dont do a lot of install/uninstall, and i kinda started out using apt-get/synaptic, so i'm sticking with it by inertia for now. :)

---

