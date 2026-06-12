---
title: "Need Mac like application switcher"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-12-02
Sure.. the compiz app switcher shift/ring/etc look cool but theres one problem!!

You can never find your application in a quick amount of time because they ALL use a rotation scheme. I like the standard linux/windows/apple app switchers/ and even vista now.. They don't rotate like a ring.. It is way easier to find what your looking for..

Is there a way to make the app switcher not rotate around.. All the icons/screenshos should stay in the same place as you select among them..

OR does anyone have a mac style app switcher??

---

### Post by systemintheglitch on 2007-12-02
Not only that..

But if you only have 2 apps open.. it shows at leaste three!!

That is so stupid! :)

I think this is one thing vista got right.

---

### Post by staticvoid on 2007-12-02
you can configer everything in ccsm. I've set mine so that the windows do not fade in and out. just click on the switcher and change its properties. you can change key bindings and everything.

sv

---

### Post by systemintheglitch on 2007-12-02
> **staticvoid said:**
> you can configer everything in ccsm. I've set mine so that the windows do not fade in and out. just click on the switcher and change its properties. you can change key bindings and everything.

sv


I know.. But it doesn't give me an option to do two things i would really like..

1. Only show icons.
2. do not rotate around in a ring.. Keep a fixed list and move  the selection along.. Of course the selection could wrap around once it gets to the end.. like on mac.

---

### Post by SunnyRabbiera on 2007-12-02
well compiz is still under development but i will say this:
no matter what bugs it has compiz is WAAAAAAAAAAAAAY better then aero the default effects manager in vista.
This is mainly from a stability standpoint, as if aero messes up it can really ruin your day.
I have seen aearo crash and it is not pretty, at least with compiz if it crashes nothing is really lost as metacity will take over.
granted some of the effects in compiz need work but if you can use a really vista butt kicking desktop effects even under 512, I have 241MB of memory and even that works well with compiz, I triple do dare you to try to run aero that low.... it wont work, me I can run compiz at lower deskop effects fairly well

---

### Post by systemintheglitch on 2007-12-02
Ya ya ya.. But i need a way to make it just show icons.. and not rotate the list around.. when selecting an application.,

---

### Post by SunnyRabbiera on 2007-12-02
ehh could be a bug in general anyhow as I have this issue.
its possible that this part of compiz needs more work from the developers.
Like I said compiz is still under development so bugs are expected... though this is not a critical one in my eyes as personally I can care less about effects...
I perfer stability and my philosophy is that stable should come before "wowee" anyday...
I think microsoft missed this message.
But OSX I admit has got both vista and compiz beat in many ways at least for the time being...
patience is a virtue grasshopper

---

### Post by systemintheglitch on 2007-12-02
No I don't think this is a bug.. It's just poor UI design.

---

### Post by GSF1200S on 2007-12-02
> **systemintheglitch said:**
> No I don't think this is a bug.. It's just poor UI design.

Do something about it then; it didnt get as good as it is right now with just complaints. I mean Mac and Vista dont have "the cube," so does that mean they suffer from poor UI design? No, of course not- 

You see, youre in a different world now- its not about what "they" put out... your free to make these necessary changes yourself if you are so inclined...

---

### Post by systemintheglitch on 2007-12-02
> **GSF1200S said:**
> Do something about it then; it didnt get as good as it is right now with just complaints. I mean Mac and Vista dont have "the cube," so does that mean they suffer from poor UI design? No, of course not- 

You see, youre in a different world now- its not about what "they" put out... your free to make these necessary changes yourself if you are so inclined...


C'mon man.. It's just not wise for me to allocate my efforts into learning how to code compiz plugins.. There's just too much to get started.. I just need a quick solution.

Does anyone know how to activate STANDARD alt+tab action while desktop effects are on.. It doesn't seem to work.

---

### Post by staticvoid on 2007-12-04
> Does anyone know how to activate STANDARD alt+tab action while desktop effects are on.. It doesn't seem to work.

Lol. Guy comes to forums and asks a question. Everyone tells him to write the code himself to make it happen. I can't help you either, but...

This will give you the .xml file that compiz configuration settings manager uses in the switcher settings.
```
sudo gedit /usr/share/compiz/switcher.xml
```

Try asking your question on these forums: [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)  maybe post it in the Configuration section.

Good luck man! 

Static V

p,s, Post your findings here :)

---

### Post by LowSky on 2007-12-04
im not on my ubuntu machine but this should help
it isn't under where you might think it is

go to compiz manager look for view port switcher should be bunched in the same category with the the cube/screen view options

in there is options to change the buttons that certain features use.

FYI beryl used to have the options you are looking for, maybe someone made a fusion plug in

---

### Post by LowSky on 2007-12-04
> **systemintheglitch said:**
> Sure.. the compiz app switcher shift/ring/etc look cool but theres one problem!!

You can never find your application in a quick amount of time because they ALL use a rotation scheme. I like the standard linux/windows/apple app switchers/ and even vista now.. They don't rotate like a ring.. It is way easier to find what your looking for..

Is there a way to make the app switcher not rotate around.. All the icons/screenshos should stay in the same place as you select among them..

OR does anyone have a mac style app switcher??

OK here is what i think you want

 you want to enable swift switcher then switch the appearance mode from cover to flip

also yo want to enable application switcher which looks like the old windows alt+tab windows

---

### Post by systemintheglitch on 2007-12-05
> **LowSky said:**
> OK here is what i think you want

 you want to enable swift switcher then switch the appearance mode from cover to flip

also yo want to enable application switcher which looks like the old windows alt+tab windows


The first part was wrong.. The second part was right..

Originally, I wanted to make the shift switcher stand still.. NOT rotate when you press alt+tab.. And also not show two applications as three (try it: open two apps press alt tab.. Shows it as three! that's confusing!)

I want it like vista and mac, where the apps stay still and your selection moves among them.

Now: given that there is no way to do that, I want to enable the standard alt+tab behavior when desktop effects is on.. Unless you know of a way to make them not rotate.

---

### Post by xarquid on 2008-07-13
There is a way to do this now, and if you have I apologize for reviving an old thread, I was actually trying to find out how to do this when I discovered it just from "messing around in CompizConfig Settings Manager.

*This is assuming you have Ubuntu 8.04+ and/or the latest Compiz and CompizConfig Settings Manager...*

[INDENT]The option you want is simply: **Ring Switcher**
Just enable it.[/INDENT]

To test it out when you first enable Ring Switcher before all of the above, just use your Windows key (it's "super" if you don't know, and hit tab). I think you'll be happy with the result. :-)

[INDENT]*Play around with the appearance tab ("Ring Appearance"), to make it look better. I had to adjust the thumbnail sizes (Width to about 600 and Height to about 450 and then I was a bit happier, a few other settings were tweaked as well). *[/INDENT]

Then just make sure: Shift Switcher / Application Switcher are disabled (IF YOU WANT)...

And you can set Ring Switcher's default to ALT + TAB for fun if you'd like (Key Binding's tab in Ring Switcher):

[INDENT]Key Bindings > Next Window (First Option) > Click It (Currently "<Super>Tab" and Just hit <Alt>TAB on your keyboard.[/INDENT]

You should be all set.

Sincerely,

Craig Huffstetler / xq
#ubuntu-us-sc / #apache / #mysql
Ubuntu Team SC

---

### Post by edfish on 2008-07-13
alt+tab works like in windows...(on my setup)

[email]edfish@live.co.uk[/email] email and msn

---

