---
title: "cube help"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by CougarisAlsar on 2007-05-24
Now, i installed beryl and everthing works like a dream, but when i want to play a game i have to turn the cube off (for some reason i just get a black screen, but thats not the problem) anyway, i go back into beryl manager and click the checkbox beside desktop cube to reactivate the cute. But i got nothing. Now, i sort of had this problem before with the feisty cube, and fixed it with gconf-editor apps->compiz->general->screen0->options hsize 4, # of desktops 1 and by the looks of other threads people have had the same problem with beryl and fixed it with that. But even after doing that i still have no cube and that makes me sad.

I have no clue what to try next, please help, thank you

---

### Post by starcraft.man on 2007-05-24
> **CougarisAlsar said:**
> Now, i installed beryl and everthing works like a dream, but when i want to play a game i have to turn the cube off (for some reason i just get a black screen, but thats not the problem) anyway, i go back into beryl manager and click the checkbox beside desktop cube to reactivate the cute. But i got nothing. Now, i sort of had this problem before with the feisty cube, and fixed it with gconf-editor apps->compiz->general->screen0->options hsize 4, # of desktops 1 and by the looks of other threads people have had the same problem with beryl and fixed it with that. But even after doing that i still have no cube and that makes me sad.

I have no clue what to try next, please help, thank you

Just a thought, but in future you really don't need to turn off the cube feature. It's really a lot easier to just go back to the metacity window manager (right click on the beryl gem > Select Window Manager > Metacity). That should save you the hassle of opening the preferences, and free a few cycles up from using beryl.

Now to your problem... I'm not sure I understand... do you mean when you reactivate the cube function of Beryl, all your screens go blank? If its only the other 3 desktops, have you tried reloading the window manager (Right Click Beryl > Reload window manager)? If that's not it, you may have to be a bit more specific, I'm not sure I follow exactly the problem...

---

### Post by CougarisAlsar on 2007-05-24
no, the problem isnt that any of the screens goes blank, the problem is that i cant get the cube to come up period. ctrl+alt+left click doesnt allow me to rotate or even bring up the cube. Likewise ctrl alt left arrow or right wont switch to a different workspace. I only seem to have one workspace.

---

### Post by Znupi on 2007-05-24
Go to **Beryl Settings Manager -> General Options** And check these options:
-- **Horizontal Virtual Size** - 4
-- **Number of Desktops** - 1

---

### Post by starcraft.man on 2007-05-24
> **CougarisAlsar said:**
> no, the problem isnt that any of the screens goes blank, the problem is that i cant get the cube to come up period. ctrl+alt+left click doesnt allow me to rotate or even bring up the cube. Likewise ctrl alt left arrow or right wont switch to a different workspace. I only seem to have one workspace.

Hmmm, very odd... lets try something.... just thinking once my beryl crashed and the manager stayed running, lets check >.>.

type this into the terminal:

```
beryl
```

simple enough, do you get any errors after that? If not try again to move the cube.

Edit: Znupi, I think he already did that... he mentioned resetting the desktops manually I believe.

---

### Post by CougarisAlsar on 2007-05-24
> **Znupi said:**
> Go to **Beryl Settings Manager -> General Options** And check these options:
-- **Horizontal Virtual Size** - 4
-- **Number of Desktops** - 1

Nah, those are all good

> **starcraft.man said:**
> Hmmm, very odd... lets try something.... just thinking once my beryl crashed and the manager stayed running, lets check >.>.

type this into the terminal:

```
beryl
```

simple enough, do you get any errors after that? If not try again to move the cube.

Edit: Znupi, I think he already did that... he mentioned resetting the desktops manually I believe.

I guess something i absent mindedly left out is that my beryl is still running perfectly EXCEPT for the nonexistant cube, i still have a theme running and wobbly windows and all that other good stuff, just not the cube. I did what you said while it was still running and it went to metacity, but i did it again and beryl came up without a hitch

---

### Post by starcraft.man on 2007-05-24
> **CougarisAlsar said:**
> 
I did what you said while it was still running and it went to metacity, but i did it again and beryl came up without a hitch

That tells me that Beryl (or part of it) crashed... and while you still had the theme and wobbly windows, it was crippled I guess.

In future, switch to metacity via the right click of the beryl gem that I mentioned in my first post, that will eliminate any issues in gaming or beryl I believe.

Oh and if this bug should persist after a reboot (I seen it in a few people where beryl crashed and refused to load with the beryl manager), just go into sessions and put in a new entry and make the command just "beryl". I believe that covers everything.

Beryl should work fine in the future have a nice day :).

---

### Post by Znupi on 2007-05-24
> **CougarisAlsar said:**
> I did what you said while it was still running and it went to metacity, but i did it again and beryl came up without a hitch

That happens to me too, even though beryl is working fine.

---

### Post by FNDII on 2007-07-13
Was there a fix? happening to me. Every thing works fine, no cube.

---

### Post by bdtgp on 2007-07-13
Go into General Options>Desktop size and set it to 4.

---

### Post by FNDII on 2007-07-13
Its set to 4 already.

This is a supposed fix 

[http://ubuntuforums.org/showthread.php?t=500427](http://ubuntuforums.org/showthread.php?t=500427)

It allowed me to move windows to other screens just by dragging them. Then Since that was theclosest thing to  amoving cube I have gotton to see, I decided to play around and seeif I couldget a cube going. 

Well not nothing works again, 4 days and no cube. Everyotherthing in Beryl but no cube anywhere

---

### Post by FNDII on 2007-07-13
Ok i just had to re do that fix, that fix was hard to find.

and why did it happen?

---

