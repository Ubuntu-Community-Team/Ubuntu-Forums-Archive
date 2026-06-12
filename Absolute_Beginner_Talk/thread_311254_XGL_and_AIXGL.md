---
title: "XGL and AIXGL"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by PatsM on 2006-12-02
What do these terms mean :confused:

---

### Post by antharr on 2006-12-02
These are terms that refer to software that adds 3-d fucntionality to your desktop. Check out the link below. There are some screenshots and short movie clips of it in action. 

[http://www.novell.com/products/desktop/features/xgl/]("http://www.novell.com/products/desktop/features/xgl/")

---

### Post by PatsM on 2006-12-02
OK. Next question; which one is the better??

---

### Post by desimo on 2006-12-03
Difficult to say.  Novell's XGL and RedHat's AIGLX perform similar tasks in different ways.  The idea is to draw windows into memory (compositing) instead of directly to your screen.  This way, windows can later be recalled and manipulated in a variety of ways...

XGL acts as a "middleman" between your current X server and the rest of your system.  Applications report to XGL, which reports to X, which reports to your screen (This is actually an oversimplification on my part, because in order to get adequate performance you have to use GL-X, which "extends" the  original X server to process calls to OpenGL in a new way better suited to pass them on to X.  It is the goal of XGL to eventually completely rewrite the X server.

AIGLX is an attempt to improve the performance of the existing X server to work with compositing.  It's basically an X server extension which communicates directly with the GPU.

I think the general consensus is that AIGLX is better (where possible) because it is more integrated (allows direct rendering by the GPU).  However, AIGLX is much harder to implement because the OpenGL drivers that allow the GPU to communicate with X need to be altered.


Edgy comes with AIGLX by default.

---

### Post by PatsM on 2006-12-03
Thanks for the clear answer; i get the picture now :)

---

