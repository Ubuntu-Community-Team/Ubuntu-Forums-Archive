---
title: "how to make copiz fusion see through"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by hershe33 on 2008-03-09
how do I make the compiz fusion cube see through

---

### Post by Joeb454 on 2008-03-09
From a terminal run ```
sudo apt-get install compizconfig-settings-manager
```

And then open that from System>Preferences>Advanced Desktop Effects Settings

You'll have a whole list of Compiz options to change :)

---

### Post by SunnyRabbiera on 2008-03-09
also for transparent windows you can install emerald...

---

### Post by Joeb454 on 2008-03-09
I think the OP wanted the Cube to be transparent...

---

### Post by hershe33 on 2008-03-09
it says E: couldn't fid package compizconfig-settings-manager

---

### Post by Joeb454 on 2008-03-09
Ok, go to System>Administration>Software Sources and enable all of them except for CD and Source Code :)

Then run the command in a terminal again, **BUT** run ```
sudo apt-get update
``` first :)

---

### Post by hershe33 on 2008-03-09
ok that worked now what do i do

---

### Post by Joeb454 on 2008-03-09
Ok so you have the Advanced Settings Manager running?

Now just go down to the cube option and choose your settings :)

---

### Post by wesley_of_course on 2008-03-09
For see-thru  I found the following to work for me ; System, Preferences, Advanced Desktop Effects Settings  - click on Desktop Cube  and you should see 5 tabs; General - Appearance - Behaviour  -Transparent Cube  -Actions .

     Click on Transparent Cubes    and Tweak to your hearts content !

     Two threads I've used extensively when getting this setup was ;
 [http://ubuntuforums.org/showthread.php?t=659282](http://ubuntuforums.org/showthread.php?t=659282)    and this website ; 

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

        Another thread I ran across was this one ; [http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)
            Most were straight forward and all took some reading and configuring but what a great way to learn , lotta fun too.  Your mileage may vary . Hope this helps and as always  post back with a tip or particular challenge , there are thousands more who are more knowledgeable  than me which makes this forum so great .      :cool:

---

