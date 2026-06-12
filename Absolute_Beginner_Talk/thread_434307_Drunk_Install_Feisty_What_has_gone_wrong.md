---
title: "Drunk Install Feisty: What has gone wrong?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by poetmayhem43 on 2007-05-05
Hi,

I decided to give Ubuntu 7.04  a proper test.  I noticed that there had been a lot of talk on the internet on how great it was and how it was really easy for 'idiot' users as it is a point and click installation.  I decided that for a proper test of this and as the important documents on the PC aren't my own (but those of my girlfriend who has threatened death if this goes wrong) that I would try an even odds install.  This meant that although my computer knowledge was poor I would make things more interesting by consuming a large quantity of alcohol (cloudy cider and white wine in this case)  and see how this affected the install process.  (I already knew that as I had an ATI Radeon Xpress 200 Series graphics card that I may have issues.)  

Surprisingly and despite the fact that I am still heavily inebriated I found that Ubuntu was really easy to install and is working as a dual XP boot.    

When I attempt Desktop Effects I get the message that 'the composite extension is not available' which at the moment I take for a good sign meaning restart and all will be well.  

That said said partner has passed out from above combination during Kevin Smith's 'Mallrats'.  Perhaps this should tell me something, but whilst the alcohol still allows 'idiot' testing conditions and whilst girlfriend doesn't know that her data is at risk (evil hangover girl is not currently being considered as an option) then I guess things are cool.  

Many  thanks too the Ubunto team.  (This is all assuming install is successful.  I of course completely lay any blame for error with Canonical and not my cider.  :) ) 

-John

---

### Post by Doug11 on 2007-05-05
I also have that same video card. The "no composite extension"  is not that serious if the eyecandy is not your thing. It more less means that you dont have direct rendering which is needed to run such proggies like beryl or compiz. But seeing as you  have installed Feisty, I do believe that you can install the correct driver for this ati card in the restricted drivers. I too am having a few Buds right now and am on Vista so i cant really tell you exactly where it is,,,could be something like system>preferences> restricted drivers. It's under that menu somewhere. Hope this is of some help.

---

### Post by picpak on 2007-05-05
Try editing your /etc/X11/xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

and putting these lines in:

```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

Then restart X by pressing Ctrl+Alt+Backspace. Hopefully then it might work.

---

### Post by pay on 2007-05-05
In Server layout you need ```
        Option          "AIGLX"         "true 
```as well as ```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

---

### Post by poetmayhem43 on 2007-05-05
Thanks PicPak, Thanks Pay.  

Pay... How do I get to 'Server layout' to add the line you specified?  I have added the part Picpak suggested and it makes progress, but not all the way.  

I sadly appear to be sobering up, but at 3am GMT I want to get this sorted before my girlfriend wakes so I can show her fancy desktop stuff.

---

### Post by Tux Aubrey on 2007-05-05
This is great - giving a drunk person terminal commands and telling them to edit xorg.conf.  Talk about living on the edge!  I think sudo privileges should only be available if you have a blood alcohol level of under .05

---

### Post by poetmayhem43 on 2007-05-05
I do hope then that for the next version Ubuntu will bring out a breathalyser test before download.  

:)

Personally I like the concept.  

As long as the terminal command instructions are given in a way that a drunk person new to Linux can understand (obviously said drunk should be 'compus mentis' enough able to type admin password) then I think that Ubuntu is perfectly usable for everyone.  

> Still not worked out the server bit or why XP doesn't boot anymore, but I suppose these points can be resolved on upgrade to Gutsy (I will continue with the cloudy cider theme on release, stay tuned).  

> Most likely they would get resolved whilst sober, but that spoils the exercise.  Wish me luck!

---

### Post by MCMcButtah on 2007-05-07
I broke my sever over the weekend installing a new drive while I was drunk....ugh. My drunken upgrades always worked when I was using windows!!! :)

---

