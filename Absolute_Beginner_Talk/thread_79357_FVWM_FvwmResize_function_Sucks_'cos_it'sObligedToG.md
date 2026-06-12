---
title: "FVWM: FvwmResize function Sucks 'cos it'sObligedToGoOutsideTheWindowToResize..."
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-20
How is it possible to make it like in fluxbox or other X-Gui????? 
Is there a script to help?
  
The problem is that u have to move the move until outside the window.
And in other Xserver, if you are in middle of the considered window, only moving the mouse can resize the window (make it bigger or smaller) ?
  
(Making smaller from being in center of window is not working, is there a solution ??)

(Mouse 3 IWTF M FvwmResizeOrRaise) 


Thank you very much 

Pat'

---

### Post by ThomasAdam on 2006-10-26
> **patrick295767 said:**
> How is it possible to make it like in fluxbox or other X-Gui????? 
Is there a script to help?
  
The problem is that u have to move the move until outside the window.
And in other Xserver, if you are in middle of the considered window, only moving the mouse can resize the window (make it bigger or smaller) ?
  
(Making smaller from being in center of window is not working, is there a solution ??)

(Mouse 3 IWTF M FvwmResizeOrRaise) 


Thank you very much 

Pat'

I have no idea what you're on about.  Assuming this issue isn't fixed, provide more details.

-- Thomas Adam

---

### Post by slimdog360 on 2006-10-26
I think I know what your talking about, if you move the mouse past the edge of the screen it goes to the next desktop. Which is annoying I know. 

Ive been using FVWM-crystal which is an entire desktop environment. In this there is an easy way to fix this, just mucking around with the borders, themes etc until you hit the right one. 

Ive only been using it on my laptop for a couple of days so I cant remember any exact technique. Download and install FVWM-crytal and follow the instructions to install it. Its not hard and you end up with a much better desktop.

---

### Post by siepo on 2006-10-30
You can maximize the window first. Then it will fit exactly on the screen, and you can get at the edges.

---

### Post by ThomasAdam on 2006-11-08
> **slimdog360 said:**
> Ive been using FVWM-crystal which is an entire desktop environment. In this there is an easy way to fix this, just mucking around with the borders, themes etc until you hit the right one.

It's not an "entire desktop environment" -- it's FVWM, which is a window manager.  Many people forget this and completley shut out many possibilities open to them as a result.

In answer to your question, look at 'EdgeResistance' and 'EdgeScroll' in 'man fvwm':

```

# EdgeScroll defines how much of the viewport is scrolled when the mouse
# hits the edge of the screen.  Tyically this might land the viewport
# in-between pages, so I tend to disable it.  Besides which, I never did
# like flipping pages with the mouse.
EdgeScroll 0 0

# EdgeResistance defines the resistance value from the edge of the
# screen when moving windows between pages.  It's useful so that you don't
# move windows from page to page when you don't mean to.
EdgeResistance 500 1

```

-- Thomas Adam

---

### Post by patrick295767 on 2006-11-12
> **ThomasAdam said:**
> It's not an "entire desktop environment" -- it's FVWM, which is a window manager.  Many people forget this and completley shut out many possibilities open to them as a result.

In answer to your question, look at 'EdgeResistance' and 'EdgeScroll' in 'man fvwm':

```

# EdgeScroll defines how much of the viewport is scrolled when the mouse
# hits the edge of the screen.  Tyically this might land the viewport
# in-between pages, so I tend to disable it.  Besides which, I never did
# like flipping pages with the mouse.
EdgeScroll 0 0

# EdgeResistance defines the resistance value from the edge of the
# screen when moving windows between pages.  It's useful so that you don't
# move windows from page to page when you don't mean to.
EdgeResistance 500 1

```
  
-- Thomas Adam


Hi,

Firstly, this is an old post and I am very sorry about the title. 
 
So, concerning the problem that was, this is due to :
  
```
Mouse 1 W       M   Move-or-Raise
Mouse 3 W       M   ResizeWarp
**AddToFunc ResizeWarp I Resize Direction SE warptoborder**

```
  
At that time, I wasnt satisfied with the resizing of Fvwm which wasnt like others windows manager (try blackbox, fluxbox, ...). After some time, you just get used and it is fine.
Above, in this fvwm example, the mouse arrows is firstly going to the edge of the window, then it is resized. 
In blackbox, for instance, the mouse arrow stays where is it when pressing  Meta Mouse 1.
  
(Ahhh)
  
Have a good day guys, 
 
Also, Thank you Thomas for your constant and accurate help in Fvwm forum; you are doing a great 'job' !

---

