---
title: "touchpad of 1215N"
date: 2011-08-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AmiNimA on 2011-08-27
Hi, I have a 1215N of ASUS, with ubuntu 11.04.  everything works great (even nvidia ION) except the touchpad. some times it works ok, but without any reason it starts annoying: single tap does as right click, and moving the mouse become difficult. I must do some hard click to fix it. but after some minutes it looses its function. 
(the touchpad is synaptic)

---

### Post by eGlyph on 2011-09-10
Confirmed. Exactly the same problem, Asus EEE PC 1215P. See [this]("http://forum.eeeuser.com/viewtopic.php?id=89461") thread.

Basically, there are two options: either move the foam pads under the trackpad (see link above for the instructions) or change driver options. 

Open terminal and issue the following:

```
$ sudo touch /etc/modprobe.d/psmouse.conf
```

Open this with your favorite editor and type (note the empty line at the end of the file):

```
options psmouse resetafter=10


```

Reboot and it's gone. All credits go to Rich.Rat from forum.eeepcusers.com

---

### Post by AmiNimA on 2011-09-11
Thank you. I will try the commands. :)

---

### Post by aliaomt on 2011-10-05
did it (software solution) solved your tochpad problem

i have this problem to and reluctant of opening it up!

---

### Post by AmiNimA on 2011-10-05
> **aliaomt said:**
> did it (software solution) solved your tochpad problem

i have this problem to and reluctant of opening it up!

NO :( it didn't solve the problem.

---

### Post by aliaomt on 2011-10-06
this works for me
 
```
rmmod psmouse
modprobe psmouse

``` 

but i must do it every time that touchpaf freez and it`s somehow anoying

is there any way to check that i do the eGlyph procedure (options psmouse resetafter=10) in the wright way? because it did not works for me too.

---

### Post by AmiNimA on 2011-10-13
you can add "modprobe psmouse" to the scheduler (cron) to run it every miute! it seems solves the problem. but this is not a solution

---

### Post by AmiNimA on 2011-11-01
try adding this line    ***psmouse proto=exps***      to the grub menu list file in your boot partition/folder, at the end of the line which starts with /boot/vmlinuz-2.6.37-6  (depending on your installation).
it seems this solved the problem! I'm not sure, but I haven't the problem so far.
lets try this for a while to see the resault!

---

### Post by AmiNimA on 2011-11-02
nope :( still no chance :(

---

### Post by AmiNimA on 2011-11-04
ok... so...
this is a physical problem made by ASUS, you must do that barbarian solution and open your touchpad. This is the only way... I did it and the problem gone.

---

### Post by dirmansyah on 2011-11-12
How did you open the touchpad and what did you do?
More info, please.
thanks.


> **AmiNimA said:**
> ok... so...
this is a physical problem made by ASUS, you must do that barbarian solution and open your touchpad. This is the only way... I did it and the problem gone.

---

### Post by AmiNimA on 2011-11-13
1-open as I showed in this picture:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207109&stc=1&d=1321205502[/IMG]

2- now with your nail (!) or a knife, try to open the case of touchpad area. (all around the area where the logoes are attached). becareful not to break the clips. no need to force alot, but becareful.

3- as this picture shows ([from this thread]("http://forum.eeeuser.com/viewtopic.php?id=89461")) paste a tape at the back of the touchpad area.(the green tape) and cut the areas which I have marked them in red

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207110&stc=1&d=1321205943[/IMG]

3- close the case and the back of the laptop. 
4- mission complete... :)

---

### Post by jeromgbh on 2011-11-28
AmiNimA,

Thank you very much for the hints !!!

Now the touchpad of my 1215n is working fine, no more crazy behavior.

---

