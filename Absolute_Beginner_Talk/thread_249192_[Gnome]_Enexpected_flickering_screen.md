---
title: "[Gnome] Enexpected flickering screen"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by S1NGH on 2006-09-02
Greetings all,
I had just installed Kubuntu last night and i wanted to get gnome so i updated my source list and insalled gnome using the command
```
sudo aptitude install ubuntu-desktop
```

Everything was working fine when i tried to install a new theme... it was working fine until i rebooted because it was lagging.
I tried to enter the gnome session and upon entering the top and bottom panels were flickering and nothing loaded. i waited for a few minutes butt nothing happened, i rebooted again and tried to go into failsafe gnome mode, unfortunately the same thing happened but an error message was displayed but i couldn't view it. the title of the message was Warning.
Does anyone know i can get my gnome desktop back without uninstalling it? as the source list and insallation too a long time!

and i wanted to know if the size of my SWAP would affect overall application performance, i.e opening, browsing, viewing files etc.
my current SWAP is 510MB, can i increase it if i want without reformating?

i am running it with a dual boot with Win XP

---

### Post by xpod on 2006-09-02
Well you certainly jumped in at the deep end eh.....:D 

Just a curiosity but that aPPtitude is just a typo is`nt it??????
I suppose if you actually GOT IT installed it must just be a typo

Well im sorry you waited all this time on the cd getting there just for you to have problems on your first day but SOME people still cant get past the
"boot from cd stage"....:-\" 

I know you dont want to reinstall but if it`s made such a mess then you dont want traces of that mess affecting eveything else so mabet a re-install would be best so as to do your partitions more to your liking and sticking with just the ONE desktop environment until you are more sure of it all?

I know how you feel though as i too like to jump into something i know nothing about then have great fun ](*,) until i figure out how to fix it.

As far as getting rid of the Gnome destop is concerned i believe that as long as you installed with "aptitude" then "sudo aptitude remove gnome desktop" should get rid of it and all packages it came with??

OR someone who KNOWS this stuff might get you running both and fixing the mess out without having to re-install.......Good luck

EDIT:im sure they WERE but you did check you were installing correct themes  for correct desktop??????..I dont know what the score is about different themes in dual-desktop environments....A clash of some sort possibly???

---

### Post by S1NGH on 2006-09-02
> **xpod said:**
> Well you certainly jumped in at the deep end eh.....:D 

Just a curiosity but that aPPtitude is just a typo is`nt it??????
I suppose if you actually GOT IT installed it must just be a typo

Well im sorry you waited all this time on the cd getting there just for you to have problems on your first day but SOME people still cant get past the
"boot from cd stage"....:-\" 

I know you dont want to reinstall but if it`s made such a mess then you dont want traces of that mess affecting eveything else so mabet a re-install would be best so as to do your partitions more to your liking and sticking with just the ONE desktop environment until you are more sure of it all?

I know how you feel though as i too like to jump into something i know nothing about then have great fun ](*,) until i figure out how to fix it.

As far as getting rid of the Gnome destop is concerned i believe that as long as you installed with "aptitude" then "sudo aptitude remove gnome desktop" should get rid of it and all packages it came with??

OR someone who KNOWS this stuff might get you running both and fixing the mess out without having to re-install.......Good luck

EDIT:im sure they WERE but you did check you were installing correct themes  for correct desktop??????..I dont know what the score is about different themes in dual-desktop environments....A clash of some sort possibly???

You are right Sir, its my typo, its aptitude :P

with problems you learn, and learning is the way to success...so i am in no doubt that i was playing around :P

> SOME people still cant get past the
"boot from cd stage"....:-\"lol... maybe they don't search and read before posting as that's what i have realised but i read the posts with a smile and just try and put my self into the situation ;)

to remove the packages with it the command is
```
sudo aptitude remove ubuntu-desktop
```
well i haven't yet tried this command as i don't want to update again, my connection is slow and takes me atleast 2 and a half hours :( so if there is a way i can save my updates i will be able to try and see what happens.

there could be a possible clash with the themes, but i was installing a GTK 2.x theme.
Murrine  GTK2 Cairo Engine 0.10

i used a .deb and did the following
> 
 -- Ubuntu *.deb --
 Go into the dir where you've saved the file and type:
 $ sudo dpkg -i package_name.deb


while i was doing it, it was all working fine but then was lagging a bit so i just rebooted by pressing the reset button on the pc and them the problem arose, so i would like to know how i can resolve it, hopefully somecon help me out soon :)

---

### Post by xpod on 2006-09-02
> while i was doing it, it was all working fine but then was lagging a bit so i just rebooted

Theer in lies the problem then is it not???

IF you rebooted while it was still carrying out the theme install......??

Im just guessing mind you.....Im off to try the xlg thing on our kubunto.THAT ones seems like its got better graphics cards than this..IT has 2 card s in there so i need to suss out whats what first...THIS only has an onboard chip off some sort for graphics.

NO doubt break it all in the process but there in lies the fun eh:rolleyes:

---

### Post by jesus of suburbia on 2006-09-02
I installed ubuntu and looved gnome but wanted kde i couldnt be bothered to install kde aswell so now ive got ubuntu, kubuntu and winxp working in dual boot!!!!! i think i might get rid of kubuntu as i think ubuntu roks the socks off kde

---

### Post by S1NGH on 2006-09-02
xpod: thats exactly what i did, rebooted while installing....
xgl is good, but i am not too sure if it'll work on kde properly.
i too am stuck with some onboard graphics chipset :P so not xgl for me :(

true about your last point, we can't live without it!

[jesus of suburbia]("http://www.ubuntuforums.org/member.php?u=145934"): ubuntu is nice but resource hungry, i think i will stay with KDE for now but i will still like to know how to sort out the problem :P that's just me!

---

### Post by xpod on 2006-09-02
Hey hey...Now im having a similar prob(have posted:-\" )
My adept package manager is refusing to work.:-D 
I killed it when it froze on the removal of some games
and now it wont let me use it.Ive even rebooted but 
no joy...

So we`re both in the same boat now from the same cd......great eh
:confused: ](*,) :twisted: :-D

---

### Post by S1NGH on 2006-09-03
> **xpod said:**
> Hey hey...Now im having a similar prob(have posted:-\" )
My adept package manager is refusing to work.:-D 
I killed it when it froze on the removal of some games
and now it wont let me use it.Ive even rebooted but 
no joy...

So we`re both in the same boat now from the same cd......great eh
:confused: ](*,) :twisted: :-D

no wonder we are one of the problem makers experts around here.
hopefully you resolve your problem, or have you done it already?

---

