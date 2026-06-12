---
title: "Blender 3D not running"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-05
Hello!
As one of my attempts to create the perfect Ubuntu system, I'm trying to install Blender 3D. I installed it (sudo apt-get install blender), and no errors were pointed out for it. However, when I go to Applications -->> Graphics -->> Blender 3D Modeller, I click the program, and it doesn't run. I can keep doing this, but it never runs. This could possibly be a graphics card problem (or something to that effect) because simple animations run slightly slower on my Ubuntu partition. I want to know if there are any other possible problems, and how to fix them (or how to find out if it's my graphics card).
Thank you!

---

### Post by robinl on 2006-10-05
run it from a terminal and see what happens. Also, did you install your graphics card's driver?

---

### Post by blendmaster on 2006-10-05
The terminal replies with:

> Error: Unable to open blender window

Where might I find my cards info (what command), and where are the drivers listed?

Thanks!

---

### Post by blendmaster on 2006-10-05
Judging from the fact that it can't open the window, I'm guessing it's more of the graphics problem. So If I were to want to install the driver, where would the driver info be?

---

### Post by robinl on 2006-10-05
Well do you know what graphics card you have? If you haven't manually installed drivers you will be using open source ones which have limited 3D acceleration and thus blender cannot be ran.

---

### Post by mysticrider92 on 2006-10-05
My PC with intergrated graphics runs Blender fine (rendering is a bit slow, but I think that is going to happen no matter what), so your card itself shouldn't have a problem opening it. I think the problem might be your X11 and GUI configuration. Knowing what graphics card you have would help also. 

I think you can use the command "lcpci" to get information on your card. If you can, tell us the name of your card a list of the screen resolutions it will allow you to use might help determine the driver you have.

---

