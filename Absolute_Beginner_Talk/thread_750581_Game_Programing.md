---
title: "Game Programing?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-09
I want to learn to design games and i heard that a good place to start is to lean python and use the panda 3d engine. So i went to the panda website and got everything set up and started following the first tutorial. I created a folder on my desktop called games and i created a file called Game.py inside the folder. Then i went into blender and created a cube to import. Then i put this code inside my Game.py file just like it says in the tutorial.

This is my exact code that i have entered from following the tutorial

import direct.directbase.DirectStart

#Load the first environment model
land=loader.loadModel("land")
environ.reparentTo(render)
land.setScale(0.25,0.25,0.25)
land.setPos(-8,42,0)

run()




This is the error i get in IDLE when i run it... i do get a screen that shows up and its just a blank screen... but i get this error message and the object does not show up in the window

DirectStart: Starting the game.
Warning: DirectNotify: category 'Interval' already exists
Traceback (most recent call last):
  File "/home/mike/Desktop/app/Game.py", line 5, in <module>
    environ.reparentTo(render)
NameError: name 'environ' is not defined


Does anyone use this engine and can tell me what im doing wrong? D=

or if anyone knows another engine i can start using to make games can you recomend it... Please make it an engine that comes with a lot of tutorials because i am new to game programming =]

---

### Post by PFSpectrum on 2008-04-09
that first part where i accidently wrote environ is not the error... i fixed that and i still get the error message

---

### Post by PFSpectrum on 2008-04-09
This is the new error message i get 

Traceback (most recent call last):
  File "/home/mike/Desktop/app/Game.py", line 5, in <module>
    land.reparentTo(render)
AttributeError: 'NoneType' object has no attribute 'reparentTo'



And this s the code in the Game.py file

import direct.directbase.DirectStart

#Load the first environment model
land=loader.loadModel("land")
land.reparentTo(render)
land.setScale(0.25,0.25,0.25)
land.setPos(-8,42,0)

run()

---

### Post by brennydoogles on 2008-04-09
Do you already know Python?? If you don't, then you should consider backing up and learning the basics of Python first. Object Oriented Programming is not necessarily Self-explanatory, and if you get ahead of yourself it can be really discouraging (as well as not being productive).

My other suggestion is to ask for this thread to be moved to the programming talk section of the Forum, because the people who could help you most are more likely to be able to help you there. Hope this helps!

---

### Post by PFSpectrum on 2008-04-09
Well i had a book on python that i read a while ago... but my friend told me to use C++ or C# instead... but those are so hard to learn =[ i just want to make a game and those languages are really hard lol... also how to i get this moved to another location? O_O

---

