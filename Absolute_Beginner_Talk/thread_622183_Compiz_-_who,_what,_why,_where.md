---
title: "Compiz - who, what, why, where?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-24
Dear Ubuntu Community,

All over this forum, I see "Compiz" pop up in almost every thread.  I finally got curious as to what it is, so I Googled it, went to the site, and also went to the Wiki entry... and still have no idea what it is.  Is it just eye candy?  Or is it actually useful?  I've seen people proclaim that it's both (and I've seen people claim it's just eye candy, too).

What I'm asking, I guess, is what is it good for?  What are some common applications it's used for?



My next question, then, would be "is it worth the effort?"  Soooooo many of the times I see "Compiz" in a thread, it's almost always associated with some deep problem.  I don't mind putting in some effort for something that might be useful, but if it's just eye candy, I wouldn't want to bother.



My final question would be (if it is worth the effort, that is), would my computer theoretically be able to handle it with little to no problem.  It's a fairly sweet computer--AMD64 Athlon X2 5600+, 2GB RAM, 500GB SATA HDD, nVidia GeForce 6150.  Is there any problem it has with integrated graphics cards, or with nVidia, or with 64 bit processors, etc.?



Thanks in advance for your answers and opinions.  (Maybe linkage to tutorials and such would be a blessing, as well.)

---

### Post by tdrusk on 2007-11-24
It's what the desktop effects are, compiz-fusion.

They are not needed for a functional desktop, but can add some functionality.

---

### Post by bluepowder7 on 2007-11-24
it's like having a Lazy Susan (you know what that is, a rotating platter) with anywhere from 2 to 32 LCD monitors on it, and you can spin it around to show any one at a time, and each has a certain set of applications showing on it.

it's a useful desktop management tool, but it also has eye candy built in.  why?  because it can.  and some like the eye candy.  it's got a lot of candy, but that means you can just pick and choose the 2 or 3 touches you want, and install those.  the rest can be disabled.

GeForece 6150 should work fine...

---

### Post by Sarteck on 2007-11-24
Is it as easy as **sudo apt-get remove compiz-fusion** to get rid of, if I decide I don't like it?  Will it mess with any configuration files I might want to backup?

---

### Post by kelbizzle on 2007-11-24
It's as easy as going to [B]System ->Preferences -> Appearance -> Visual Effects
[/B]

It depends on how often your on the computer or how much of a nut your are about saving time by eliminating time spent doing repetitive things, number of clicks, length of motion. I love the [scale]("http://www.youtube.com/watch?v=-LsrocISlyQ") feature It's just like apples Expose. I also find it easy to Hold alt+scroll to make my console window transparent so I don't have to flip back and forth when inputting commands. Or I don't have to minimize my chat windows when I'm watching a movie because I can see right through them.  I also like the group and tab feature keeps multiple windows together in a nice clean way. Give it a go...and find YOUR uses for it. It does save some time. It's also fun to play with when your bored.

---

### Post by bluepowder7 on 2007-11-24
Alt+[scroll] - now THAT'S cool!  i didn't even know about that.  haha!  that's a pretty nifty "stealth" feature to hide some of my windows when i step away from the computer.  lovely!

how did you find out about that feature?  where can i learn the other 'tricks'?  was it in the main control panel of that manager???

---

### Post by kelbizzle on 2007-11-24
> **bluepowder7 said:**
> Alt+[scroll] - now THAT'S cool!  i didn't even know about that.  haha!  that's a pretty nifty "stealth" feature to hide some of my windows when i step away from the computer.  lovely!

how did you find out about that feature?  where can i learn the other 'tricks'?  was it in the main control panel of that manager???

I'm like a kid when it comes to software. I just snooped around just about every option I could click on. I've been using it since the beginning and I found what works for me. 

In the Compiz Config tool..General Options -> Actions Opacity.

---

### Post by HermanAB on 2007-11-24
Compiz is nice if you have a decent gamer rig with a good video card.  However, after spending some hours getting it to work, you will likely tire of it in about 2 minutes flat, since there is no blood, guts, gore or sound effects...

So, in short, it isn't really worth the trouble, but then what is?

---

### Post by bluepowder7 on 2007-11-24
ooh, ok.  so i assume that "Button 4" and "Button 5" are equivalent to scroll-up and scroll-down?  cool.  i thought they were separate controls and i needed a monsterous multi-button-from-hell mouse to use the features.  cool!  learned somethin' new today!

---

### Post by akiratheoni on 2007-11-24
> **bluepowder7 said:**
> Alt+[scroll] - now THAT'S cool!  i didn't even know about that.  haha!  that's a pretty nifty "stealth" feature to hide some of my windows when i step away from the computer.  lovely!

how did you find out about that feature?  where can i learn the other 'tricks'?  was it in the main control panel of that manager???

Actually you can 'hide' your windows with Tab and Grouping, that way you can tab your windows... it's really cool, actually.

---

### Post by bluepowder7 on 2007-11-24
> **HermanAB said:**
> Compiz is nice if you have a decent gamer rig with a good video card.  However, after spending some hours getting it to work, you will likely tire of it in about 2 minutes flat, since there is no blood, guts, gore or sound effects...

So, in short, it isn't really worth the trouble, but then what is?

there's a flamethrower!!!  you can burn windows and paint over Britney Spears' face with a torch.  that's GOTTA be worth an install...

---

### Post by jingo811 on 2007-11-24
> **Sarteck said:**
> Is it as easy as **sudo apt-get remove compiz-fusion** to get rid of, if I decide I don't like it?  Will it mess with any configuration files I might want to backup?

Yeah it's easy to remove with apt-get there's more dependecy packages that will need to be removed though on top of what you wrote.  But since you're using Gutsy you won't have to mess with such things it's already taken care for compared to us Feisty users.

Compiz Fusion is like what you can see on Windows Vista and Mac OSX desktops.  The difference is when the Desktop breaks in Windows not sure about Mac OS you'll need to re-install your entire operating system.
If Compiz Fusion breaks you just replace it with some regular Desktop manager like GNOME, KDE, Xfce, Fluxbox, etc. etc. with something like this.  That way you won't have to re-install your entire Ubuntu just the Desktop manager.
```
sudo apt-get install gdm ubuntu-desktop
```
[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

All you need to do as a Gutsy users is configure your Hardware by following the hardware link in this website.  No extra installations required.
[http://wiki.compiz-fusion.org/Welcome](http://wiki.compiz-fusion.org/Welcome)

If running Compiz Fusion breaks your window manager just run this in Terminal and you'll get GNOME back.
```
metacity --replace &
```

---

### Post by WarningXdezzy on 2007-11-24
I love my desktop affects, but it does make a person a bit screen shot crazy! 
The picture below is  an XGL cube on a dell inspiron 1100..it's like 5 years old and it works flawlessly[IMG]http://bp3.blogger.com/_doIc7ntaMc8/R0NjL93T_FI/AAAAAAAAAAo/xK9sGXWZ3GU/s320/xglshot.png[/IMG]

---

### Post by stefanza on 2007-11-24
It's definitely worth it - but you can find yourself spending a lot of time playing with settings for the best effects.  A short cut to a great setup can be achieved by following this blog.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by DutyDuty on 2007-11-24
It's also good for showing up people who are in love with how "cool" their OSX effects are. 

> You've got a minimize shrink effect? I've got a freakin' CUBE.

---

### Post by wingmanjd on 2007-12-21
> **WarningXdezzy said:**
> I love my desktop affects, but it does make a person a bit screen shot crazy! 
The picture below is  an XGL cube on a dell inspiron 1100..it's like 5 years old and it works flawlessly[IMG]http://bp3.blogger.com/_doIc7ntaMc8/R0NjL93T_FI/AAAAAAAAAAo/xK9sGXWZ3GU/s320/xglshot.png[/IMG]

I'm attempting to get compiz to work on my Inspiron 1100.  Seeing that you got yours to work, could you help me get mine to work?

---

### Post by Pogeymanz on 2007-12-21
So, correct me if I'm wrong. I always thought Compiz was an extra tool, but they way you talk it sounds like is is actually a whole desktop interface. If you install Compiz, does that mean you are not using Gnome/KDE/Xfce?

---

### Post by jingo811 on 2007-12-21
If I understand things correctly. 
[http://xwinman.org/index.php](http://xwinman.org/index.php)

[LIST]
[*]X11=X is the foundation on which you build your house.
[*]Floor 1: Window Managers (WM)= metacity, fluxbox, etc. etc.
[*]Floor 2: Desktop Environments (DE)= Gnome, Kde, Xfce
[/LIST]

Gnome have the Window Manager metacity included in the background.   When you setup you hardware and then manages to install Compiz Fusion correctly (don't ask me how) and start it up.  Then you're using the WM Compiz Fusion instead of Gnome's default WM metacity.

If Compiz Fusion gives you graphical or navigational problems then you just simply use Terminal and switch off the WM and instead start the default metacity WM.  (again don't ask me how) it was some time ago I did all this.  But when you switches the WMs you never have to reboot your PC.

That's the difference between Linux and Windows.  If Windows Desktop breaks then it will take the entire /root system down with the fall so to speak :)  When Linux Desktop breaks it's just the Desktop and the WM that falls.  Not your /root system.

---

