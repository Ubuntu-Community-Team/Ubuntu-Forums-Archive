---
title: "[SOLVED] never run compiz?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-31
Is there a way to never run Compiz, It is running cause there is black at the x server log in..It slows my computer down and id rather never run it, but ive heard that if i never run it, my window borders will be messed up..setting the desktop to none doesnt work..

My question is how can i completely never run compiz and when I do, with Metacity take its place?

---

### Post by Inxsible on 2008-03-31
I am guessing you still want to use the restricted drivers tho. Go to System>>Preferences>>appearances. Go to the Visual Effects tab and select the None radio button. That disables compiz and makes metacity as your default

---

### Post by sports fan Matt on 2008-03-31
I'll try this again but last time i did, it appeared to be still running since i had a black background before  my desktop, which im pretty sure isnt normal..

Edit:  Black background before my desktop loaded and the visual effects tab was ticked to none..That means if im still seeinbg the black background i assume im still running compiz, which shouldnt be cause the tab is ticked to none..

Am i missing/overlooking something??

---

### Post by Inxsible on 2008-03-31
are you sure the black background is only because of compiz and nothing else?

---

### Post by sports fan Matt on 2008-03-31
Im not..I thought it was Compiz that slowed things down...What other things can i check?

---

### Post by sports fan Matt on 2008-03-31
I do know my machine doesnt require any restricted drivers "Your hardware does not need any restricted drivers".

---

### Post by Inxsible on 2008-03-31
> **sox fan Matt said:**
> Im not..I thought it was Compiz that slowed things down...What other things can i check?
just so I am clear, what black background are you talking about ? does it cover the entire screen or just the bottom section ?

Black screens at the bottom have been known to be caused by docks like Kiba and even AWN. Oh and if you are running one of those docks, then you definitely need to have compiz switched on, or you will see the black bar near the bottom of the screen.

---

### Post by sports fan Matt on 2008-03-31
I do have awn manager installed ..if i can ditch that i think thats part of the issue..and it covers the entire screen till my desktop starts

---

### Post by Inxsible on 2008-03-31
> **sox fan Matt said:**
> I do have awn manager installed ..if i can ditch that i think thats part of the issue..and it covers the entire screen till my desktop starts Just having it installed shouldnt matter, Have you put Awn Manager in your startup programs?

If you have, then the reason most likely is that your AWN is starting up before your compiz does and so you see the black screen. You might have to change the order of compiz and awn. 

Let me know if you even have those in the startup programs first before I give you a solution for it.

---

### Post by sports fan Matt on 2008-03-31
I have Avant Window Navagatior in the startup programs but it is not enabled and there is nothing about Awn in my startups...

---

### Post by Inxsible on 2008-03-31
> **sox fan Matt said:**
> I have Avant Window Navagatior in the startup programs but it is not enabled and there is nothing about Awn in my startups...
Ok. Go to System>>Preferences>>Sessions. Go to the Current Session tab and then select compiz from the list of processes. Change the order of the process to something lower like 10, say (that's what I have set it to).

What this will do is, it will load compiz before anything else and that way awn will get loaded after compiz and you shouldn't see the black screen.

The screen is temporary even now, correct?

---

### Post by sports fan Matt on 2008-03-31
Right...Let me restart the desktop and see

---

### Post by Inxsible on 2008-03-31
> **sox fan Matt said:**
> Right...Let me restart the desktop and seeGood luck, fingers crossed :)

---

### Post by sports fan Matt on 2008-03-31
still a black screen after i restarted till my desktop but i discovered something..I didnt see anything about compiz, but I did see metacity and lowered it to 10..

I have a deskbar applet running and a fast user switcher applpet running in my current programs..i will list them

-session properties gnome
-vino session -sm-config-prefix/vino session
-metacity
-gnome panel
-gnome volume manager
-nautillius
-power manager
-update manager
-pidgin display
-gnome power manager
-Avant Window Navagator
There that is...that could be the cause...

There are other processes running...let me know if u need them

---

### Post by Inxsible on 2008-03-31
See now that's the whole problem. If you are going to start up AWN, you need to start Compiz. Without which AWN gives black screens.

So re-enable compiz and then make sure you change the order for Compiz to 10 or anything lower than what AWN is at.

Another way could be that you gotta get rid of Avant Window Navigator from the startup list as well.

---

### Post by FreewareFan on 2008-03-31
Hey Matt, me again.  Have you tried a program called Kooldock?  I dumped AWN for Kooldock over a week ago, and haven't looked back since.

If you like Kooldock, then you wouldn't have to worry about compiz or AWN anymore.  Just a thought.....

---

### Post by Inxsible on 2008-03-31
> **FreewareFan said:**
> Hey Matt, me again.  Have you tried a program called Kooldock?  I dumped AWN for Kooldock over a week ago, and haven't looked back since.

If you like Kooldock, then you wouldn't have to worry about compiz or AWN anymore.  Just a thought.....
The last time I used KoolDock, it kept crashing on me a million times. It has the cool fish eye effect of the mac os docks tho :)

---

### Post by FreewareFan on 2008-03-31
Been rock-steady for me on Ubuntu Gutsy.  Couldn't ask for more from a dock program...  It loads very fast, very small footprint, and like you said, great eyecandy!

---

### Post by sports fan Matt on 2008-03-31
I re enabled compiz to normal and installed Kooldock...Lets see what occurs

---

### Post by FreewareFan on 2008-03-31
Don't forget to disable AWN tho...  lol

---

### Post by Inxsible on 2008-03-31
> **sox fan Matt said:**
> I re enabled compiz to normal and installed Kooldock...Lets see what occurs
Do you still have AWN switched on ?

I don't think you need Compiz for KoolDock, but no harm having it either.

---

### Post by Inxsible on 2008-03-31
> **FreewareFan said:**
> Don't forget to disable AWN tho...  lolAs long as he has compiz running, awn shouldnt give him any problems

---

### Post by FreewareFan on 2008-03-31
> **Inxsible said:**
> As long as he has compiz running, awn shouldnt give him any problems

Well, if both docks are running, they are going to bump heads, yes?  Yes.  I found that out by experience...

---

### Post by Matthewslf on 2008-03-31
Why not uninstall AWN?

---

### Post by FreewareFan on 2008-03-31
Hey Matt, one thing about Kooldock.  You need to keep at least one launcher icon on it, so that it runs correctly.  I tried to remove all those launcher icons that it came with, and it gave me a bunch of error messages when I restared it.  So, as long as you keep at least one launcher icon on the dock, you're good to go. Just choose a launcher icon from the programs that you like, and use that as the place-holder.

---

### Post by FreewareFan on 2008-03-31
> **Matthewslf said:**
> Why not uninstall AWN?

Because at this point, he is just experimenting with things, to see what he likes best.  So, if he only disables awn, he doesn't have to go thru the motions of re-installing it again, if he decides that he likes it best after all....

---

### Post by sports fan Matt on 2008-03-31
Upon further investigation under sessions>Current Avant Window Navagator is currently running and the value to the left is 50..that seems like a very high number or am i wrong?

---

### Post by FreewareFan on 2008-04-01
> **sox fan Matt said:**
> Upon further investigation under sessions>Current Avant Window Navagator is currently running and the value to the left is 50..that seems like a very high number or am i wrong?

Nope.  Most of my currently running apps are at 50, so I believe that's really the norm.

OK bud, I'm outta here for the night.  Hope things work out well for ya, and let me know what you ultimately think of Kooldock, will ya?  Later....

---

### Post by Inxsible on 2008-04-01
> **sox fan Matt said:**
> Upon further investigation under sessions>Current Avant Window Navagator is currently running and the value to the left is 50..that seems like a very high number or am i wrong?and what is the value of compiz?

---

### Post by sports fan Matt on 2008-04-01
The value at left was 50...

---

### Post by Inxsible on 2008-04-01
> **sox fan Matt said:**
> The value at left was 50...MAke sure the value of compiz is LESS than the value of AWN.

That will load compiz before it will load AWN. Then you should not see the black screen AFAIK.

I don't think I can get any clearer than that.

---

### Post by sports fan Matt on 2008-04-05
All fixed..I completely have no black screen and all i did was get rid of xorg something...

---

