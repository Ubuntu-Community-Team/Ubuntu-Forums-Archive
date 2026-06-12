---
title: "What program to use?"
date: 2008-01-23
forum: Art &amp; Design
---

### Post by Valok on 2008-01-23
I just started looking at the pictures that people can make with blender and I was absolutely astonished by some of them.  That said, I really wanna get into making some images of my own.

What program should I use to make them?  I've only seen blender images but I'm sure there are other similar (maybe better) programs out there.

Are there any other programs that I should get to supplement an image program that I might use?

---

### Post by Paul820 on 2008-01-23
Blender is capable of producing top quality models, animation and even games so why not start with that? It's free and open source and constantly improving thanks to the dedicated developers. It doesn't cost you anything to try it out. If you want to try something else, nothing comes close to blender in the free software category, so you will have to dig into those pockets and pay some cash. Most of the 3D software out there is for windows and can cost you from a few hundred to a few thousand dollars.

---

### Post by dmn_clown on 2008-01-29
> **Paul820 said:**
> Blender is capable of producing top quality models, animation and even games so why not start with that?

Actually it's not.  If it were, the large Hollywood studios would use it for production purposes and they don't.  Please see:  [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html) where you'll find > Blender and Wings3D are not used in production because they are considered inadequate for the needs of Hollywood. Blender has been used for pre-viz development for the Spider-Man movies, but not production. The cheapest 3D modeler that's widely used in commercial movies is SoftImage XSI. That starts at $500 and is a more powerful tool than OSS 3D apps. 

That's not to say that Blender is a bad program, it just has its limitations and the community should be honest about them (and work to improve them).  

For creating 3d rendered images apart from blender you can use:
- KPOVModeller (a front end to POVRay)
- K-3d (a Gtk-based modelling program that is fully Renderman compliant and less imposing than Blender, but packages of aqsis the recommended renderer may be difficult to find)
- K3dsurf (another POVRay "modeller")

---

### Post by pieisgood on 2008-01-29
dmn_clown: You're right, Hollywood has no association with programs. They let the artists pretty much use what they please. Valok is a beginner. He doesn't even want to wade into the realm of Renderman and POVray and command line renders. 

Hollywood also doesn't use linux as some sort of almighty artists tool. They aren't forcing the modelers and sculptors to run Autodesk products or Z-brush under wine or emulation. 

Maya
Max
Zbrush
MudBox
XSI

doesn't matter, they are running them on windows. Linux is used for something else. Video editing is done by snobs on MACs.

also, elephants dream


Valok: Start using blender, learn the keys and look for modeling tutorials. You can learn how to model in tons of ways using Sub-D, extrusion or any combination of modeling techniques under Blender. All the same basic modeling concepts apply to it as they do to every other 3D app. I picked blender up just a few days ago and once I learned the hot keys for modeling I was pumping out the polys. You're a beginner so the hotkeys should make a lot of things easier. Concentrate on the sections you want to learn one at a time. It doesn't help to have ADD when it comes to learning these programs as people specialize in certain areas of them, animation, rendering, lighting, modeling, detailing, texturing. blah blah blah... yeah use Blender at first and then maybe move onto incorporating Z-brush into your production pipe to add serious details... but that comes later.

---

### Post by digitalis_vulgaris on 2008-01-29
From open source 3d application Blender is the best solution. This program has it all you need to produce professional looking 3d. Still isn't in class with XSI, but it has a fast development progress - I believe it's just a matter of time...
If I need something only for modeling, Wing3d would be my choice. This application have the most reliable treatment of mesh geometry. Even better than in XSI. But this application miss some modeling techniques and some features which would make it a great software.

:popcorn:

---

### Post by dmn_clown on 2008-01-29
> **pieisgood said:**
> Hollywood also doesn't use linux as some sort of almighty artists tool.

Yeah, they use it because of the cost involved, which is to say none if they have a good IT admin, slightly more if they go for the "supported" linux model with a less skilled admin.  Which means that the bulk of their workstation costs go into the graphic tools (most of which have been ported). 

You are wrong about needing to know the command line to use POVRay (or Yafray for that matter) with KPOVModeler and k3dsurf, all of the rendering options are handled in the client with no CLI knowledge required.

k-3d is a very good choice for a beginner to learn, it aims to be as easy to use as wings3d (and is very close in those terms) and can use any of the main rendering solutions (POVRay, Yafray, Aqsis, Pixie, etc.)  Something that the OP asked for that wasn't Blender.  

Just a note (so you know that I am not bashing Blender) that I do use Blender but I am not at all going to recommend it as a program to learn the basics of 3d modeling, wings3d or k-3d are better choices there with k-3d giving the better rendering options (again what the OP asked for).

---

### Post by eye208 on 2008-01-29
> **dmn_clown said:**
> Actually it's not.  If it were, the large Hollywood studios would use it for production purposes and they don't.
Blender's capability has [already been proven](http://www.elephantsdream.org/). Of course that doesn't mean Hollywood is going to switch tomorrow. CGI is the cheapest part of moviemaking anyway. If you want to cut production cost, the CGI department is the last place to look at. You would rather extend it so you can save money elsewhere.

With its current pace of development, Blender will sooner or later become the #1 tool for CG animation. That's also because for many upcoming CGI artists Blender will be the first tool they learn to use.

---

### Post by digitalis_vulgaris on 2008-01-29
Except Blender you cannot find a lots of applications which are made for 64bit OS with multithreading support.

---

### Post by Paul820 on 2008-01-29
> Actually it's not. If it were, the large Hollywood studios would use it for production purposes and they don't. Please see: [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html) where you'll find

I don't need to see, i have seen enough top quality work by many people from all over the internet. I agree blender is not quite there yet but that doesn't mean it isn't capable. As **eye208** already pointed out, take a look at elephants dream. **Valok** is a beginner, i don't think he will be working for dreamworks just yet do you? So i think blender is a great starting point.

---

### Post by dmn_clown on 2008-01-29
> **digitalis_vulgaris said:**
> Except Blender you cannot find a lots of applications which are made for 64bit OS with multithreading support.

k-3d handles that just fine.

[quote=eye208]With its current pace of development, Blender will sooner or later become the #1 tool for CG animation.[/quote]

Not if they don't fix its memory management.  A 300,000 poly model shouldn't bring a system to a stand still.

---

