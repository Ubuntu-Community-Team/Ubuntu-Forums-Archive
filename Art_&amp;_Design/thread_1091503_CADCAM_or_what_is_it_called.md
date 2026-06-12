---
title: "CAD/CAM or what is it called?"
date: 2009-03-09
forum: Art &amp; Design
---

### Post by ecm_z28 on 2009-03-09
i want a program to make 2d manual build/machineing drawings, so i get specified lenght and width of everything, i'm not intrested in a 3d drawing, because this is for making drawings of measures how i'm going to build stuff in the machine shop..

sorry for the bad technical english but i hope someone understands what im looking for.. :)

---

### Post by Peter76 on 2009-03-09
You are looking for Qcad; it is in the repos. It's a very good but easy 2d cad program

---

### Post by ecm_z28 on 2009-03-09
thanks gonna test that one.. :)

it's the one i'm after, thanks alot Peter76

---

### Post by ecm_z28 on 2009-03-09
i just cant get it.. no matter how i do, i just cant get any precision into the boxes, it have to be possible to assign a rectangle is 400x400mm and a circle is 300mm in diameter, but i just cant figure out how to do that easy.. otherwise its gonna take ages just to do a simple drawing with measures of a box for subwoofer? because the measures tool is so good but to get that to work you have to get the rest to have good measures otherwise it wont work ;)

---

### Post by Peter76 on 2009-03-09
uhmm, it sounds like you have no CAD ecperience at all ??? ( no offense intended :-) ) Or am I wrong? What you want is actually what cad is all about, but it will be a very very long answer to explain here. If you install qcad-doc ( or something like that ) you get a very basic qcad manual. Google for qcad tutorial and you get some tutorials. I can also suggest buying the commercialversion and/or the book; it is very cheap and the book is a very good introduction to cad in general. If you run into some more specific problems, post back and I'll try to be of help.

Good luck, Peter

---

### Post by ecm_z28 on 2009-03-09
> **Peter76 said:**
> uhmm, it sounds like you have no CAD ecperience at all ??? ( no offense intended :-) ) Or am I wrong? What you want is actually what cad is all about, but it will be a very very long answer to explain here. If you install qcad-doc ( or something like that ) you get a very basic qcad manual. Google for qcad tutorial and you get some tutorials. I can also suggest buying the commercialversion and/or the book; it is very cheap and the book is a very good introduction to cad in general. If you run into some more specific problems, post back and I'll try to be of help.

Good luck, Peter

yep your right, i got no clue about cad.. but i can write manually on paper a build draw on atleast half complex mechanical stuff, i just dont get the cad tools.. i've spent the last hour i guess reading the doc that came with qcad, and i just cant find what i'm looking for i guess, i've got limited knowledge from 3dmax and some from Z-modeller, modelling cars.

the problem i got is i place a rectangle, and make it ~400x400 then i want the next rectangle to be 430x430mm and i want to move it so i get 15mm on all edges, but this is where it stops, when i get confused.. because i cant seem to make the 4 vertex'es into one singel box so i can edit the box'es preferences and sizes (like i would do in 3dmax, just that i dont have any windows computer anymore so i'm kinda in deep **** as the trunkbuild for amps and subwoofers is already begun, and i've would have hoped that 2009 i wouldn't have to do it manually, but it does look that way hehe.. 

gonna have a look at those qcad tut's and hopefully i find something good.. :)

/Björn

---

### Post by Peter76 on 2009-03-09
A very simple tutorial then:-) Hope this will get you started enough... In your main toolbuttons at the left of the drawing window click:
line-tool -> rectangle 
	-> click somewhere in window; this gives first point of rectangle.

Now, In the bottom of the qcad window you see a message: Specify second corner . Click after corner, the text will turn blue.
 now enter : @400,400 These are coordinates, the 400 is the measurement you want ( whatever unit !!! ) and the @ means it's relative to your last used point. ( without the @ it means relative to the zero of the coordinate system. )

So now you got your inside rectangle. I f you can't completely see it, click on the zoom button ( magnifying glass ) with the black square in the top of the window. This will zoom out to everything you have drawn so far.
 To get your outside rectangle, click on the arrow above your toolbuttons on the left till you get your main toolbuttons. Click on line-tools-> parallel ( 7th one ). Somewhere at the top-left it now says: distance: xxxxx. Enter 15 here( Bet you get where we are going.) ( you can also enter it at the bottom where you entered the @400,400; just remember to click there if it isn't blue. Hit enter.
Now click just outside of the lines of the square you have drawn so far. You will get a line parallel to your original line at the given distance, in this case 15.

Now to connect these lines in the corners, click the back arrow on top of your tool buttons again till you are back at the main tool buttons. Click edit-> trim/extend two ( 8th button ). Click on the lines which you want to connect close to the corner, et voila!

Well, this was a VERY basic intro to cad, but you will find Qcad very easy to learn, and as said, I can really recommend the qcad book. ( I am not affiliated with qcad :-) ) See [www.ribbonsoft.com](www.ribbonsoft.com).

Good luck

---

### Post by ecm_z28 on 2009-03-10
> **Peter76 said:**
> A very simple tutorial then:-) Hope this will get you started enough... In your main toolbuttons at the left of the drawing window click:
line-tool -> rectangle 
	-> click somewhere in window; this gives first point of rectangle.

Now, In the bottom of the qcad window you see a message: Specify second corner . Click after corner, the text will turn blue.
 now enter : @400,400 These are coordinates, the 400 is the measurement you want ( whatever unit !!! ) and the @ means it's relative to your last used point. ( without the @ it means relative to the zero of the coordinate system. )

So now you got your inside rectangle. I f you can't completely see it, click on the zoom button ( magnifying glass ) with the black square in the top of the window. This will zoom out to everything you have drawn so far.
 To get your outside rectangle, click on the arrow above your toolbuttons on the left till you get your main toolbuttons. Click on line-tools-> parallel ( 7th one ). Somewhere at the top-left it now says: distance: xxxxx. Enter 15 here( Bet you get where we are going.) ( you can also enter it at the bottom where you entered the @400,400; just remember to click there if it isn't blue. Hit enter.
Now click just outside of the lines of the square you have drawn so far. You will get a line parallel to your original line at the given distance, in this case 15.

Now to connect these lines in the corners, click the back arrow on top of your tool buttons again till you are back at the main tool buttons. Click edit-> trim/extend two ( 8th button ). Click on the lines which you want to connect close to the corner, et voila!

Well, this was a VERY basic intro to cad, but you will find Qcad very easy to learn, and as said, I can really recommend the qcad book. ( I am not affiliated with qcad :-) ) See [www.ribbonsoft.com](www.ribbonsoft.com).

Good luck

i see.. well i was to stupid to accually understand that i did right, but i feelt i was going over the bridge to fetch water.. :D

well it's not that hard when you toy around abit with it..its just that you cant use the good old 3dmax way of doing stuff, fast create then modify to right size then move them where you want it.. :)

guess its just a matter of learning it right.. :)

Thanks alot Peter, and hopefully i'll pick on myself from here.. :)

ps. gonna have a look at that qcad book.. :)

---

### Post by Peter76 on 2009-03-10
I bet there are much quicker ways of doing this, but Qcad is the only good working cad app now under Linux, and my cad needs aren't that big:-) Good luck!

---

