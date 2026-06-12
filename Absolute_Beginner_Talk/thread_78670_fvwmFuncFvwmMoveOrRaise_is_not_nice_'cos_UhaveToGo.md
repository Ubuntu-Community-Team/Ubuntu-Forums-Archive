---
title: "fvwm:FuncFvwmMoveOrRaise is not nice 'cos UhaveToGoOutsideWindow ToResize:SthgBetter?"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-18
fvwm:FuncFvwmMoveOrRaise is not nice 'cos UhaveToGoOutsideWindow ToResize:SthgBetter?

I would like to change FuncFvwmMoveOrRaise in the .fvwmrc2 by sthg taht would work like in   fluxbox for instance ... to resize the window wihtout having to go outside of this window (like in fluxbox).

Is there a genius who can let me know how to make the function or find the solution ?

Thank you very much, 

Patrick !

  
  
  
 My mouse config:
I used : 
# some simple default mouse bindings:
#   for the root window:
Mouse 1 R       A       Menu MenuFvwmRoot Nop
Mouse 2 R       A       Menu MenuFvwmWindowOps Nop
Mouse 3 R       A       WindowList

#   for the title bar buttons:
Mouse 0 1       A       Menu MenuFvwmWindowOps2 Close
Mouse 0 2       A       FuncFvwmMaximize
Mouse 0 4       A       Iconify

#   for other parts of the window/borders/icons:
##Mouse 1 F       A       FuncFvwmResizeOrRaise
##Mouse 1 TS      A       FuncFvwmMoveOrRaise

Mouse 1		WFST	1	FuncFvwmMoveOrRaise
Mouse 1		WFST	12	FuncFvwmMoveOrRaise

Mouse 1 I       A       FuncFvwmMoveOrIconify
Mouse 2 I       A       Iconify
Mouse 2 FST     A       Menu MenuFvwmWindowOps2 Nop

## Mouse 3 TSIF    A       RaiseLower
Mouse 3		WFST	1	FuncFvwmResizeOrRaise
Mouse 3		WFST	12	FuncFvwmResizeOrRaise

---

