---
title: "Could you convert graphics libraries?"
date: 2014-10-06
forum: Any Other OS
---

### Post by Jaym29 on 2014-10-06
I'm not sure if this is the correct place I should post this, but I have a pretty technical question.

By the way, I know there might be a better place to post a question like this but most fourms I've went to are not anywhere near as friendly as ubuntufourms and I think that is a major achivement for you guys :p.

Anyways, the question I have is about graphics libraries, specifically like OpenGL, and DirectX.
I'm gonna try to word this as clearly as I can.

Lets say I have a OpenGL 3.0 game, and I had a GPU that only supported OpenGL 1.0-2.0, and I wanted to play this newer game on my older hardware. What I'm mainly concerned with is if you can convert, or at least disable things like shaders (because of really old GPUS that don't even have shaders) and decrease polygon count to minimize polygon load on the GPU, And maybe even downgrade texture resolution. Make it older OpenGL, essentially.

Then to add to that, could you convert shaders to fixed pipeline?

Could it at least be plausible?

This question might seem very dumb but I just want some insight on this topic so maybe it can shed some light on the projects I might want to start.

Thank you guys very much :)

---

### Post by TheFu on 2014-10-06
If you have the game source code and both the expertise and the time to do the porting work, sure.

Chances are that it is impractical and would take 6+ months for a team of programmers already familiar with the game code.

Ok - so before some tells me I'm too pessimistic (again), you could create an API layer like they've done with WINE - which has built many of the Win32 APIs for Linux so that lots of Windows programs can be run. WINE is not a complete win32 API implementation, so not all Windows programs will work.

Libraries like this are usually backwards compatible - so v3 will support all the functions from the v2 and v1 versions of that same library.  If the program was built with relocatable objects inside the .so files, then swapping in a newer version of any library should work.  Taking a program written for a newer standard and trying to make it work on an other standard is usually not possible.

Anyway, hope that helps.

---

### Post by Jaym29 on 2014-10-06
> **TheFu said:**
> 

Ok - so before some tells me I'm too pessimistic (again), you could create an API layer like they've done with WINE - which has built many of the Win32 APIs for Linux so that lots of Windows programs can be run. WINE is not a complete win32 API implementation, so not all Windows programs will work.

.

I think this is a great idea. Thank you!

---

### Post by grahammechanical on 2014-10-09
If you were looking at a game that had as a requirement the need for DirectX 10 compliance but your graphic adapter was only compliant with DirectX 8 or DirectX 9, what would you think? It is the same with graphic adapters being compliant with OpenGL standards.

If it was possible to do what you want then it would be a different game, would it not? Chances are that it is not just the GPU that is under specified for the software.

Regards.

---

