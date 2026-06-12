---
title: "internet, java ?????"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by brianC on 2006-09-08
About a year ago I started using linux based OS .Started with  Knoppix live then moved to Ubuntu 5.05 , Kubuntu, and then loaded SuSe 10.0  DSL worked fine. After using KDE I switched back to Gnome. Updated to Ubuntu 6.06 and instantly noticed that my DSL had turned to 56k. Many days of research, and finally it almost performs like the DSL I have.....almost.
    I find that if direct address to some websites ,they won't load
    Use a search engine to search for the site, loads fine.
    Direct address stalls at ...about..90% loading site, hit refresh loads site completely 
 I have done all the suggestion from the forums(ivp6 thingy,disable pango,about:config config,faster fox,change MTU,etc,etc) and a few more ,all helped
    I have two sites that I need to visit that I cannot load.....most of the time. Both of these sites use  Java........lotsa Java.
   Installed j2re1.4
             j2re1.4-mozilla-plugin
             java-common
             java-gcj-compat
             sun-java5-bin
             sun-java5-jre
             sun-java5-plugin
I have noticed that the Javascript console is full of errors visiting these pages.
    If someone could  try to access canada.com and motovan.com and see if they have these problems.
    I am thinking that this is a Java scripting problem? 
 Not complaining,this is actually abit of fun........sittin' on the dock of the bay kind of thingy  8)

---

### Post by Tamihania on 2006-09-09
...ok - may I suggest you to check your flash plugins? I could open the pages you mentioned and they are full of macromedia commercials...
Anyway - I have flashplugin-nonfree installed + changed the code in firefox as they advise on Launchpad....

I hope it will help,
tami

---

### Post by brianC on 2006-09-09
Have flashplugin-nonfree installed not sure what is meant by 
"changed the code in firefox as they advise on Launchpad...."

---

### Post by brianC on 2006-09-10
Fixed 
  Went to GRC.com and did a port scan all but a handful of ports were reported closed, maybe 8 were stealth. Installed firestarter went back to GRC.com......all ports stealth. Now I can access all sites I couldn't before.:biggrin:

---

### Post by Tamihania on 2006-09-10
For the first - sorry to be late with the answer - I've just got an e-mail with the thread... :(
For the second - I'm glad you solved your problem :)
...and last but not least for all the others "fighting" ;) with flash in browser - here is the link to the bug I was : [bug #35942]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/35942")
The solution I used is from there:
> 

Just try and adding

XLIB_SKIP_ARGB_VISUALS=1
export XLIB_SKIP_ARGB_VISUALS

at the begining of the firefox script works well.
 
I know it will not help you... sorry to be too late... Anyway - perhaps it will help others looking for the solution...even if it's not 100% clean ;)

Friendly regards,
tami

---

