---
title: "reinstalling"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Josey on 2006-09-28
Well as a new ubuntu user I want to understand it better so maybe someone can help me clear a few things up.

Well I am pretty decent at fixing problems in windows and as most of you know sometimes it just needs to be reinstalled. 

Is that the case with ubuntu also or is it a matter of finding out why certain things are crashing. Also how do I start fresh so to speak?
Where are the important folders I should back up from all the things I have installed now? I'd like to be able to backup this stuff as net connections here arent so great.

The reason I ask this is Konqueror is crashing alot in kde and x11 won't load at all. It said gnome-volume-manager & gnome-power-manager crashed or aren't loading.

I should say that I think after I installed ubuntu, installing as many other desktop enviroments as I could and switching between them daily was a bad idea. Is it good to only have one installed at a time so there are no conflicts and such?

Gnome is the only one working right and I'm happy with using just it as I have left windows completely for ubuntu. It feels good :)
I don't want kde and x11 just sitting on my machine broken though.


 I guess my main question here is, What is a good way to go about fixing kde & x11 session types? reinstalling? how is this done?

---

### Post by petri on 2006-09-28
Maybe you should uninstall kubuntu-desktop and xubuntu-desktop? Here is a [howto]("http://www.psychocats.net/ubuntu/puregnome") for you. There is a lot of text but just copy and paste in terminal. You know you can copy by highlighting with your left mousebutton and paste it with clicking your scrollwheel?

And then if you want one of those back take a look at [this]("http://www.psychocats.net/ubuntu/aptitude") why you should always use **aptitude** instead of **apt-get**. Always.

As you might have noticed they both came from the same website, take a closer look at it too ;)

Your first but not the main question: I think the only folder to save is your **/home**. When I do an dist-upgrade or a new install (soon with edgy :) ) I wipe everything but my **/home** because I like to have everything new 8) At the same site you can read about how to make an own partition for your **/home** or take a look at my sig. But remember, you do have to be careful if you decide to do it. It can broke your system if you don't use your own **hda*** **hdb*** etc instead of the howtos ***hda7*** If you brake your system with it use your LiveCD and browse here and search first an answer, if you don't find one then start a thread.

---

### Post by K.Mandla on 2006-09-28
I know there's a "fix a broken installation" option on the alternate/install CD, but I only used it once a very long time ago, so I can't give much advice on it.

I reinstall fairly frequently, but I often deliberately try to break things. :) I learn best that way: Break, try to fix, then reinstall and break and fix again. :mrgreen:

---

### Post by Josey on 2006-09-28
Thanks for the quick replies.

> I reinstall fairly frequently, but I often deliberately try to break things. 

Yeah that's mostly why I ran rampant on this OS. For a "crash course" so to speak.

---

### Post by Josey on 2006-09-28
> Both aptitude and apt-get will install kword and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies

This is really useful as I tried to reinstall both kde-desktop and x11 with synaptic but it didn't seem to do anything and I knew that it was because it didnt reinstall dependencies. I have no idea what dependency needed reinstalling though.

Thanks again.

---

