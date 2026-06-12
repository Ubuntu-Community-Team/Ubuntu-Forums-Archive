---
title: "Blender face fgon help (2.49-2.5)"
date: 2010-02-17
forum: Art &amp; Design
---

### Post by Psychodox on 2010-02-17
Hello eva bodeh

I'm trying to find a way to add single vertices and/or edges in blender to more detailed models. I have a lot of experience in Max and Maya, but stopped using them .. about month ago now. While learning Blender I've gotten to the point where I'm attempting to merge some faces together using fgon, adding a cut to a face, and adding single vertices on a line.

Is there anyway to get an 'fgon' face to a regular face? I've looked for days, and this is probably my last option at this point. While playing with the new Blender 2.5 Alpha I couldn't even find fgon anymore and it was stated that in v2.5:

*"The face creation tool (fkey) no longer pops up a menu.  Instead, it either dissolves faces, creates faces from a collection of wire edges (an "edge net"), creates a triangle or a quad from three or four vertices, or creates an edge from two vertices.  Only one of these actions occurs, depending on context."*

So apparently fgon may be removed from 2.5, or replaced by another tool(s), I hope.

With 2.5 getting closer to Beta, this may seem a lost cause at this point; however, I was trying to refine my talents for [Durian]("http://durian.blender.org/") if nothing else it will help me push myself. 

Thanks for any help :D

---

### Post by hessiess on 2010-02-18
Don't use fgons, they are fake ngons made of triangles and don't subdivide or deform well. You can remove them by deleting the fgon and manually tessellating the hole with quads/triangles.

There is a project known as bmesh which is adding true ngons to Blender. But its requires substantial change to the code base and is tacking a long time to complete.

---

### Post by Psychodox on 2010-02-18
I've seen others looking for the same thing. Looks as though with BMesh and Blender v2.5 something relatively soon will address this. Wont really make any difference for Durian, but now I can focus on my quality and speed in Blender for now :D!!

Thanks!

---

