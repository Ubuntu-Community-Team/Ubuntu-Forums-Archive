---
title: "Linux newbie..."
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by KaIIen on 2006-11-03
Ok, a few questions.....I am running the newest 6.1 version (Edgy?)...
1. Why can I not change my desktop background? I have tried both right clicking on the desktop and selecting "change background" and I have tried by navigating to System>Preference>Change Background but nothing happens...
2. Is it possible to change my screen size through the software? Specifically, the screen size being displayed is not the same as the viewable area of my monitor....it's slightly smaller so there's a bit of "black frame" around the display. i know, I can adjust this on the monitor itself, but then when I boot to Windows it will be messed up there. 
3. Is there somewhere I can download/install software, besides the default Add/Remove Application?
4. Is it possible to use software designed for the Linspire distro? (Dumb question but i seriously don't know)
Thanks
-K

---

### Post by aysiu on 2006-11-03
> **KaIIen said:**
> 
1. Why can I not change my desktop background? I have tried both right clicking on the desktop and selecting "change background" and I have tried by navigating to System>Preference>Change Background but nothing happens... I don't know. That's not normal.

Has it always been like this (since you installed it), or is it a recent occurrence? > 2. Is it possible to change my screen size through the software? Specifically, the screen size being displayed is not the same as the viewable area of my monitor....it's slightly smaller so there's a bit of "black frame" around the display. i know, I can adjust this on the monitor itself, but then when I boot to Windows it will be messed up there.  Maybe something [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) can help you with that. > 3. Is there somewhere I can download/install software, besides the default Add/Remove Application? Yes. Read this: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) > 4. Is it possible to use software designed for the Linspire distro? (Dumb question but i seriously don't know)
Thanks
-K You cannot use CNR on Ubuntu, but most of the software available for Linspire is also available for Ubuntu. Read the link I posted above about installing software.

---

### Post by igknighted on 2006-11-03
;) not to be picky, but it's Ubuntu 6.10 (the 6 is for 2006, the 10 is because it was released in October)

as for your questions:
1) This is a really weird error, and I'm not entirely sure what might be causing this.  I would say perhaps try opening the picture you want as a background in a browser window and right clicking it and selecting set as desktop background.  I am not sure what might be causing this though.

2) To my knowledge, no, there is no software way to do this.  If you have an LCD there is probably an auto adjust button which will do it for you though.

3) There are many ways!  There are two other package managers (a little more complicated, but more powerful) called adept and synaptic.  Synaptic is installed and in System -> Administration.  You can also download source code and compile, or download .deb binary packages.

4) As far as Linspire software, anything .tar.gz or .deb *should* work (I say should because you may run into dependency issues, I don't know much about Linspire, but I think it is debian based like Ubuntu).  If it is CNR software I do not think it is compatible.  If you really want a CNR replacement you could try Klik, I have used it with Sabayon but I prefer to just install programs natively to my system.

Hope this helps!

---

### Post by jaytek13 on 2006-11-03
I have found myself that when I alter my screen in a new Linux installation it has absolutely no affect on my windows installation (perhaps it adjusts itself to the moniter? I'm not sure). So you may actually want to try this method if you haven't.

---

### Post by SunnyRabbiera on 2006-11-03
> **KaIIen said:**
> Ok, a few questions.....I am running the newest 6.1 version (Edgy?)...
1. Why can I not change my desktop background? I have tried both right clicking on the desktop and selecting "change background" and I have tried by navigating to System>Preference>Change Background but nothing happens...
2. Is it possible to change my screen size through the software? Specifically, the screen size being displayed is not the same as the viewable area of my monitor....it's slightly smaller so there's a bit of "black frame" around the display. i know, I can adjust this on the monitor itself, but then when I boot to Windows it will be messed up there. 
3. Is there somewhere I can download/install software, besides the default Add/Remove Application?
4. Is it possible to use software designed for the Linspire distro? (Dumb question but i seriously don't know)
Thanks
-K

First: do you have it actually indstalled are you still on live CD?
2: pretty much there are a few things in the repo's that can help out with resolution problems.
3: Yes, there is a neat little tool in Ubuntu called synaptic package manager that does things more efficiantly then the add/ remove software app.
4: I would not suggest it, as even though linspire is debian based its packages can cause conflicts. If you see a software that is not availible in ubuntu's repos that is not a MS app (dont excpect microsoft office or IE in the repo's) you can try converting a RPM by using a little terminal app called alien, its not on the system by default so you will have to install it with synaptic.

Any other suggestions I can give now is that if Edgy doesnt work out try dapper instead as dapper is the more stable of the two at the moment (edgy is called edgy for a reason)

---

