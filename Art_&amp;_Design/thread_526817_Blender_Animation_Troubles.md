---
title: "Blender Animation Troubles"
date: 2007-08-15
forum: Art &amp; Design
---

### Post by King_Critter on 2007-08-15
I've just started learning how to do animation in Blender, and have run into a little snag. I've successfully made and animated a robotic arm (you can see it [here]("http://kingcritter.pyrom.net/uploads/moving-arm.avi")) but now I want to make the claw pick something up. The only realistic way I can think of to do that is make a child/parent relationship. Unfortunately, I can't figure out how to turn on and off the child/parent thing in the middle of an animation. 

If you help me, I'll give you a cookie. :)

---

### Post by ghevan on 2007-08-16
You made me test this over, since I will need it some day. Ive really never done something very complex lately but after doing some test ive come up with this.

Create an empty (name wathever) and parent it to the hand, that way it will follow the hand forever. next i the object you want to "take" add to it a constrain. (in the animation tab). to my test (2d in blender) I used constrain "location", and constrain it to the empty. That way you will have it paste it to the hand. now open th IPO curve, for the object to be taken and just add a curve for the constrain that is created.  use zero influence if you want your object to be in the original position, and use 1.000 influence to have it stick to the hand. Now if you want to drop it anywhere in the scene my only tougths for this technique is to create a new empty to the final location ob the object and just change influences of the constrain (zero to "wathever" and 1.000 to the empty in the new object's position)

It ain't complex to achieve. Its just that iM not really sure that this is the correct way of doing it =p.

---

### Post by King_Critter on 2007-08-16
Alright, I'll try that. Haven't tried most of the stuff you taled about, though, so we'l see how it goes. 

/me gives ghevan a cookie

---

### Post by King_Critter on 2007-08-17
Mkay, I did what you suggested, but ran into a hitch regarding adding the constraint. Can you specify *exactly* what you did at that point?

---

### Post by ghevan on 2007-08-18
Umm you might want to try to look upon my blend file. I didn't undertand well the exact part where you are stuck. =\

---

### Post by King_Critter on 2007-08-19
*gives ghevan a whole *plate* of cookies*

w00t! I just hadn't understood the whole general idea of constraints, but after looking at your example I figured it out. Thanks. ^_^

---

