---
title: "3D Animation of simple Polyhedrons and Molecules"
date: 2011-02-26
forum: Art &amp; Design
---

### Post by schievelbein on 2011-02-26
I am looking all over for a program that will let me draw simple polyhedrons in 3D space, for dice with numbers on each side, preferably using simple commands. I then want to be able to duplicate the shape, for example, have 10 6-sided dice in a row.  The last thing I want to be able to do is program some rules, such as if I move a dice from side '1' facing forward to side '4' facing forward, then the dice to the left rotates on the X axis, and the dice to the right rotates on the Y axis. 

I have different molecules that have different magnetic properties that I want to program the interactions with, and see how they react when I start having dozens of polyhedrons and the 100s of associated actions.

I have searched under '3D State Models' and 'Molecular Animations' and many similar things, but I must be missing it somewhere.  Any and all suggestions are welcomed.

---

### Post by BcRich on 2011-02-26
Have you looked into setting this up with Blender, using the blender game engine and logic bricks?

---

### Post by V_Kaotika on 2011-03-01
Hi, maybe these things could be interesting to you...
[COLOR=DarkOrchid]
"Processing is an open source programming language and environment for          people who want to create images, animations, and interactions."[/COLOR]
Can download from here--> [http://www.processing.org/](http://www.processing.org/)

[COLOR=DarkOrchid]"**Pure Data** (or **Pd**) is a **real-time graphical programming environment** for **audio**, **video**, and **graphical processing**.  Pure Data is commonly used for live music performance, VeeJaying, sound  effects, composition, audio analysis, interfacing with sensors, using  cameras, controlling robots or even interacting with websites."[/COLOR]
You can get it thru Synaptics... looking for installing PD or PD Extended
Manuals---> [http://en.flossmanuals.net/PureData/Introduction](http://en.flossmanuals.net/PureData/Introduction)

I'm trying them now so I don't know if it can do exactly what you want... 
Good luck!

---

### Post by BcRich on 2011-03-01
ha ha why didn't I think of that :)
Processing is a great suggestion V_Kaotika!

don't know if this is what u lookin for schievelbein , but maybe it's a start?
you'll need Processing installed to run this "sketch"

```

float mPos;
int ofs = 60;

void setup(){
  size(300,300,P3D);
  
}

void draw(){
  background(127);
  mPos = map(mouseX, 0, width, 0, TWO_PI);

//white cube
  pushMatrix();
  translate(ofs, ofs);
  rotateY(mPos);
  fill(255);
  box(40);
  fill(0);
  text("1", -10, 20, 20);
  popMatrix();

//red cube  
  pushMatrix();
  translate(ofs*2, ofs);
  rotateX(mPos);
  fill(255,0,0);
  box(40);
  fill(0);
  text("2", -10, 20, 20);
  popMatrix();

//blue cube  
  pushMatrix();
  translate(ofs*3, ofs);
  rotateZ(mPos);
  fill(0,0,255);
  box(40);
  fill(0);
  text("3", -10, 20, 20);
  popMatrix();
    
}

```

---

### Post by schievelbein on 2011-03-02
Thank you very much BCRich
This will give me a good start and I will see f I can make it go from there.
This is the farthest that I have gotten in a year of research.

Michael

---

### Post by BcRich on 2011-03-02
Hi
No Problems, hope it helps.
if you are starting out with code Processing is a great language to learn, and develop with. i wrote a quickstart guide for those that have used other programming languages interested in Processing here
[http://www.lyndondaniels.com/2010/learn/processing/processing.html](http://www.lyndondaniels.com/2010/learn/processing/processing.html)
and you can also find an absolute beginners guide here
[http://www.lyndondaniels.com/programmingintro/AnIntroductionToProgrammingWithProcessing01_PartI.pdf](http://www.lyndondaniels.com/programmingintro/AnIntroductionToProgrammingWithProcessing01_PartI.pdf)
and Part2 here
[http://www.lyndondaniels.com/programmingintro/AnIntroductionToProgrammingWithProcessing01_PartII.pdf](http://www.lyndondaniels.com/programmingintro/AnIntroductionToProgrammingWithProcessing01_PartII.pdf)

---

