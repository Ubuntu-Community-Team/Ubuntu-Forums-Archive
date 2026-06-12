---
title: "Combine Two Images In Command Line"
date: 2009-12-04
forum: Art &amp; Design
---

### Post by cubeist on 2009-12-04
Hi,
I am writing a bash script and am stumped by a seemingly simple problem.  I want to combine two images into one image with a 70 percent overlay.  To better explain, here is my current gimp workflow:

-open gimp
-load two separate images into layers (one image per layer)
-move slider to a 70% overlay
-merge layers (aka flatten image)
-save as one image

Is it possible to do this via the command line?

Surprisingly there are no references on the web to this specific problem, Please Help!

---

### Post by Isaacgallegos on 2009-12-04
Haha! 
I've been a graphic artist for many years and I'd also like to know how to do this. edit: for my resume.

---

### Post by ghost1227 on 2009-12-04
This can be done using the composite tool supplied with imagemagick. 

The command I used was:
```
composite -blend 30 metalflower.png linux.png result.png
```

This command can certainly be used for more complex mergings, but I just wanted to give you a simple example to start with. Happy editing!

---

### Post by cubeist on 2009-12-04
> **ghost1227 said:**
> This can be done using the composite tool supplied with imagemagick. I used this technique to make the following (crappy) example image:


The command I used was:
```
composite -blend 30 metalflower.png linux.png result.png
```

This command can certainly be used for more complex mergings, but I just wanted to give you a simple example to start with. Happy editing!

THANK YOU!!  I knew there had to be a simple answer! You rock!

---

### Post by ghost1227 on 2009-12-04
> **cubeist said:**
> thank you!!  I knew there had to be a simple answer! You rock!

np :p

---

### Post by Isaacgallegos on 2009-12-04
sweet!! thanks.

---

