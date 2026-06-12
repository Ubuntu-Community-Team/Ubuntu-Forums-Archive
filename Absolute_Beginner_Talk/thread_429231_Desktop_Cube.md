---
title: "Desktop Cube"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-05-01
I can't figure out how to use the Desktop Cube, or at least I don't think it's being used right.

When I press ctrl + alt + left or right it will "flip" over to the left or right.  But I can't see a "cube" like the name implies.  This feature is really confusing me.

---

### Post by NikoC on 2007-05-01
And if you press ctrl + alt and hold the left mouse button thereby moving your mouse?

---

### Post by useResa on 2007-05-01
You can see the "cube" if you keep <ctrl> and <alt> pressed and move your mouse (forward to zoom out, backward to zoom in, left and right to rotate).

Success and enjoy ;)

---

### Post by JacobRogers on 2007-05-01
Is the fact that I'm using a laptop somehow stopping me from doing this?  Because I'm using a laptop.

---

### Post by eentonig on 2007-05-01
No, I have it running with a laptop.

As said. Normally <ctrl>+<Alt>+ <Left mousebutton> should show you the cube. Does that doesn't work for you? 

If that doesn't work, are the other beryl effects working? Did you verify if the keyboard shortcuts in beryl-manager are still assigned to this effect?

---

### Post by JacobRogers on 2007-05-01
I tried pluggin in a real mouse and trying the ctrl alt thing, that didn't work either.  darn.  Any help guys?

---

### Post by useResa on 2007-05-01
> **JacobRogers said:**
> I tried pluggin in a real mouse and trying the ctrl alt thing, that didn't work either.  darn.  Any help guys?Oops, sorry  :(
I indeed forgot to indicate that you have to also keep your left mouse button pressed in order for the cube to appear.

Whether or not you are using a laptop should not make a difference, I also use a laptop (Dell Latitude D620) and it works fine.
Where have you indicated that you would like to have the cube?
In System --> Preferences --> Desktop Effects?

---

### Post by JacobRogers on 2007-05-01
> **useResa said:**
> Oops, sorry  :(
I indeed forgot to indicate that you have to also keep your left mouse button pressed in order for the cube to appear.

Whether or not you are using a laptop should not make a difference, I also use a laptop (Dell Latitude D620) and it works fine.
Where have you indicated that you would like to have the cube?
In System --> Preferences --> Desktop Effects?

Yes.  At first I could get it to "flip" in a kind of 2d way, but now it won't even do that.  Lol computers.
I'm gonna keep playing with it.


Does the thing in the panel that says how many desktops you have, have anything to do with this?  Should I set it to a certain number or delete it or something?

The wobbly windows will work for me, but I think they're stupid.

---

### Post by useResa on 2007-05-01
> **JacobRogers said:**
> Yes.  At first I could get it to "flip" in a kind of 2d way, but now it won't even do that.  Lol computers.
I'm gonna keep playing with it.


Does the thing in the panel that says how many desktops you have, have anything to do with this?  Should I set it to a certain number or delete it or something?

The wobbly windows will work for me, but I think they're stupid.
I have to confirm that it now also stopped working for me.
It seems indeed that when I enable "Workspaces on a cube" I also have only one workspace left (can be seen in bottom right corner).

Searching the "net" I came across [this post]("http://forum.ubuntu-nl.org/topic/9490") (_*in Dutch*_) on the Dutch UF which pointed me towards  [this link]("http://blogbeebe.blogspot.com/2007/04/ubuntu-704-steady-updates-fixes-work.html")
> **Compiz**

It should be noted up front before I get started that Compiz stability issues are known to be a problem even by Mark Shuttleworth. But I still like to tinker with it anyway, if for no other reason that it works well under Suse. In any event I found a work-around for getting the cube effect to work again, and it involves these steps:[LIST=1]
[*]Bring up Desktop Effects and enable it if it isn't enabled already.
[*]Disable the 'Workspaces on a Cube' check box.
[*]The workspace switcher has shrunken down to one desktop. Right-click on it and configure it to have four workspaces again.
[*]Re-enable the 'Workspaces on a Cube' check box.
[*]Enjoy the cube effect.[/LIST]I tried this on both my regular login and with a test login that I created fresh for just this purpose.However, for me it does not do the trick (yet). Guess something has changed.

[COLOR=Red]**EDIT:**[/COLOR]
Have been searching the bugs and it has been reported. The workaround that got it working for me again is to issue the following commands (one at a time) in the terminal
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
``````
 gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

**The reported related bugs I found were [#82957]("https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/82957") and [#89786]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/89786")**

I hope the workaround will also work for you ;)

---

### Post by JacobRogers on 2007-05-01
That got it working for me too.

I'll play with this for a while, but I think I'm going to wind up turning it off, it's kind of hooky and doesn't seem to serve any real practical purpose.  I'm used to have having two desktops and clicking on them to switch back and forth, This new things involves all this finger acrobatics!

---

### Post by useResa on 2007-05-01
> **JacobRogers said:**
> That got it working for me too.
Glad that it solved it for you too  ;)

> **JacobRogers said:**
>  I'll play with this for a while, but I think I'm going to wind up turning it off, it's kind of hooky and doesn't seem to serve any real practical purpose.  I'm used to have having two desktops and clicking on them to switch back and forth, This new things involves all this finger acrobatics!:lolflag:

---

### Post by Malta paul on 2007-05-01
Thanks guys for the answers about  how to see the cube, now I know and it works! :guitar:

---

### Post by davecahill on 2007-05-04
This fix worked for me too, thanks!

---

### Post by ticopelp on 2007-05-04
> **JacobRogers said:**
> That got it working for me too.

I'll play with this for a while, but I think I'm going to wind up turning it off, it's kind of hooky and doesn't seem to serve any real practical purpose.  I'm used to have having two desktops and clicking on them to switch back and forth, This new things involves all this finger acrobatics!

Awesome eye-candy isn't a practical purpose? :confused:

---

### Post by NovaNine on 2007-05-07
Hey ! This solved my problem too :D

Thanks all !

---

### Post by antonius1 on 2007-06-14
Thank you that helped I really liked the cubed desktop

---

### Post by Nezing on 2007-06-14
Oh dear.I read all the answers here,and my "cube" does zip.I've repeated all the steps,and even made sure I'm pressing the correct keyboard keys (and left mouse button).
Is the effect still buggy,or am I just unlucky?  :-({|=

---

### Post by useResa on 2007-06-15
> **Nezing said:**
> Oh dear.I read all the answers here,and my "cube" does zip.
I've repeated all the steps,and even made sure I'm pressing the correct keyboard keys (and left mouse button).
Is the effect still buggy,or am I just unlucky? :-({|=
Are you indicating that your cube is NOT working at all or is it working but not as you would have liked?

---

### Post by Nezing on 2007-06-15
Nope.It's not working at all.I've tried ticking the correct "effect",in Desktop Effects,unticking it,rebooting the system,etc.The "Wobble" effect is fine (hooray),but it's the cube effect I want.I know my keyboard,and mouse are fine (I would not be writing this otherwise),and ctrl+Alt,plus  mouse are ok.System bug?:(

---

### Post by useResa on 2007-06-15
> **Nezing said:**
> Nope.It's not working at all.I've tried ticking the correct "effect",in Desktop Effects,unticking it,rebooting the system,etc.The "Wobble" effect is fine (hooray),but it's the cube effect I want.I know my keyboard,and mouse are fine (I would not be writing this otherwise),and ctrl+Alt,plus mouse are ok.System bug?:(
If you look in the bottom right corner of your screen, how many desktops are indicated there (for example see attachment)? One or more than one?

---

### Post by Nezing on 2007-06-15
I used to have just one,but adjusted to four desktops.Nope.Still nothing happening.I still think it's a system bug.:???:

---

### Post by Nezing on 2007-06-17
Okey it's been two days now,and as I've been "Ubunting",I decided to come back to the Cube.Beryl installed,nvidia driver,etc,desktop effects ticked,saved settings.Wobble,as I said before is fine,but no cube.I even changed my mouse (the old one still works fine),but no joy.I still say it's a system bug (for me :) ).
I know others have it working fine.I've seen vids on You Tube of it working,I even saw a great one being used on PC Linux,which looked cool.Me.I'm just going to stick to the "wobble",and leave it at that.

---

### Post by crisiulian on 2007-06-26
Thank you. 

Now the cube effect is working. I have 7.04 and until now only the window effects was activated. 

Thank's. 

Cristian

---

### Post by jnewm on 2007-08-19
Thanks so much for posting the fix.  Worked for me too :).

---

### Post by gcarrillo on 2007-08-24
I can confirm this workaround.

---

### Post by linksys101 on 2007-09-18
My desktop cube all of a sudden stopped working. Here is what I did to fix it. I disabled workspaces on a cube, then In the bottom right corner there was only 1 workspace. I right-clicked on the workspace and went to preferences and I changed the number of workspaces to 3, then I re-enabled workspaces on a cube and it is working again.

---

### Post by Thor (Hammer of God) on 2007-11-09
> **ticopelp said:**
> Awesome eye-candy isn't a practical purpose? :confused:
A bit late, but one should note that (assuming you've got multiple workspaces configured properly) that you don't have to <Ctrl>+<Alt>+LMouse to manipulate the cube -- simoultaneously clicking (and holding) RMouse+LMouse on the desktop and moving works as well, and I find it a much more effective way to cube-through workspaces.

t

---

### Post by CanonKen on 2007-11-09
> **Thor (Hammer of God) said:**
> A bit late, but one should note that (assuming you've got multiple workspaces configured properly) that you don't have to <Ctrl>+<Alt>+LMouse to manipulate the cube -- simoultaneously clicking (and holding) RMouse+LMouse on the desktop and moving works as well, and I find it a much more effective way to cube-through workspaces.

tWhy use two buttons when you can do it by pressing (not rolling) the scroll wheel :)
But it only works on desktop and not when a window is open

---

### Post by sailor2001 on 2007-11-09
noone said what they are using..compiz or beryl.  There is a manager for each and you can set it up as you please. I always use 6 sides..also use z as keystroke binding for rotate(in Beryl) ctrl/alt and then left click for compiz rotate..

---

### Post by DVANDERM on 2007-11-15
This is my first post and it is to say THANK YOU for posting the fix. I really like the cube to help me with organizing my workspaces. 

:KS

---

### Post by dysolve on 2007-11-16
hello all thanks for the post finally got the cube working, but is  it possible to make the cube smaller so it takes up only 2/3 of the screen that would look good.. I also found something called SHIFT SWITCHER, its like alt-tab, but you use windows button-tab instead with a cool effect..

---

### Post by siftride on 2007-11-20
OK I i have the latest version of ubuntu.  I have the cube enabled on Compiz however evertime i do alt ctrl left click its dragging the mouse and creating the shadow box in whatever shape it command it to do.  How do you get the cube to work Any help please.  Be easy im a beginner.

---

### Post by Jammerdelray on 2007-11-27
I had a similar problem, no cube effect even tho it was checked and rotate cube was as well. Under general options then desktop size, change horizontal virtual size to 4 and voila.

---

### Post by Jake90 on 2008-01-20
How many workspaces do you have? Because it won't work with less than 4

---

### Post by useResa on 2008-01-21
> **Jake90 said:**
> How many workspaces do you have? Because it won't work with less than 4Basically it works with every value over 1. However, with 2 desktops they will be stuck to each other and it still looks flat. From 3 desktops onward you will get "body" in the cube (see attachment).

You can also go over 4 desktops but than it is no longer exactly a cube.
A sample with 5 desktops is also attached.

---

### Post by bluepaddle on 2008-03-20
For what it's worth, i found the configuration of workspaces affects the cube effect.  For example, when I originally had my workspaces set to 2 columns by 2 rows, I didn't get the desired cube effect, it was simply a floating 2 dimensional portrait-type thing.  Then, I changed my workspaces to be 4 columns by 1 row and the cube appeared!  Also, a 3x1 gives a neat pyramid effect, while 8x1 does an octagon-like effect, and so on.  

It seems that the number of columns needs to be 3 or more while the number of rows is irrelevant. 

Hope this helps!

---

### Post by durableapostle on 2008-05-14
> ...I changed my workspaces to be 4 columns by 1 row and the cube appeared!
That's it! Such a simple fix... imagine that! Hard to have a cube with only 2 workspaces.....](*,)

---

