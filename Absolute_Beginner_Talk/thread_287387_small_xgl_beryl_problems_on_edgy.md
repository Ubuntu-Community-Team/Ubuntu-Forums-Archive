---
title: "small xgl beryl problems on edgy"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-10-28
I've used this guide to install xgl/beryl on edgy :
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)
and all gone quite well
but when I log to xgl/beryl session the window borders are switching constantly between gnome and xgl
I need to turn off gnome...or something  
how do I do it ? , so it always work when I run xgl session ?

2.my xgl/beryl session is S-L-O-W as HELL , much slower then it was on dapper
why ? what can I do ?
3.and it consumes LOTS of CPU usage , much more then it was on dapper.
why ? what can I do ?

---

### Post by MaximB on 2006-10-29
help still needed

---

### Post by hyby on 2006-10-29
im new to ubutun, but once you sucessfully install beryl/xgl, at your login screen you change it to XGL. This is only the case if you have added the XGL link to your session menu. 

I found that my laptop with intel 915gm did not work so well with XGL, AIGXL works a treat. XGL i believe works soley of your vid cards 3d capabilities. Whereas, aiglx is software driven. 

I found aixgl flies and i do not get a CPU load spike easily. I even sat in fron of my monitor for the whole day and let it kept spinning. Wasn't bad. Althuogh my alladin was a bit slow, but once you have  few progs up its all fine.


Therefore, in short use Aiglx!

---

### Post by MaximB on 2006-10-29
but it did work in dapper (XGL not berayl).

by the way I have ATI radeon 9800 Pro , 1 GB of RAM , 1800Mhz...

---

### Post by useResa on 2006-10-29
I had exactly the same problem (flickering windows and slow as H-E-doublehockeysticks ;)).

All my problems where solved when I stopped using the 2.6.17-10-386 kernel and started using the 2.6.17-10-generic kernel.

BTW: I do not use the additional XGL session, but use my regular session and start beryl-manager using alt-f2

---

### Post by MaximB on 2006-10-29
maxim@maxim:~$ uname -r
2.6.17-10-generic

I already have it...
and still doesn't work as it should

---

### Post by slibuntu on 2006-10-29
i have the same problem, if you go into the beryl manager, and change the theme, it works properly then but a permanent fix would be nice!

---

### Post by MaximB on 2006-10-29
actually it was the first thing that I did cuz it worked in dapper for me.
but now it doesn't work...I think it's b/z of beryl...and I used compiz in dapper.

---

### Post by MaximB on 2006-10-31
it's like 2 window manager are running at the same time

---

### Post by rlozano on 2006-10-31
maxddark, i have seen that problem sometime, (the flickering one). one i did, when i was testing beryl in my ibm notebook with ATI graphics, i would quit beryl manager, then the flickering would stop using the emerald theme, then i will just restart beryl...

useResa, your beryl is working on a normal gnome session? without any XGL session?

---

### Post by useResa on 2006-11-01
> **rlozano said:**
> 
useResa, your beryl is working on a normal gnome session? without any XGL session?
The flickering stopped after I changed over to the generic kernel.
I still do occasionally have black screens (as described [here]("http://bugs.beryl-project.org/ticket/489")).

Have not yet taken any action on that matter, but will try the suggestions as made in the final post on this matter.

---

### Post by mattgaunt on 2006-11-01
Heya

I had the flickering window problem as well

I read in a thread on the beryl site where someone said it was because there were 2 emerald window decorators running at the same time

Trick was to us

kill all emerald && emerald

Or something along those lines, dnt quote me on it cos im still pretty new at all this, but it is a temporary fix

---

### Post by Myk0n on 2006-11-01
My XGL/BERYL dont write @'s... Anyone does know how to solve this problem?
I'm using an european keyboard.. pt_PT :)

---

### Post by Myk0n on 2006-11-01
setxkbmap pt
:)

---

